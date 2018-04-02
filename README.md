# ca-edx-theme

openedX Theme for Craft Academy

## Apply theme on an openedX installation

1. Connect to the server `ssh deploy@server_ip_address`
2. Switch to `edxapp` user and load the python env

    ```bash
    sudo su edxapp -s /bin/bash
    cd ~
    source edxapp_env
    cd edx-platform
    ```

3. Get the theme

    ```bash
    ~/edx-platform $ cd themes
    ~/edx-platform/themes $ git clone http://github.com/craftacademy/ca-edx-theme.git craftacademy
    ```

    In case your already have the theme installed, just switch to the directory where the theme is stored and pull the latest changes from github.

4. Compile the theme (still as `edxapp` user)

    ```bash
    $ cd ~/edx-platform
    ~/edx-platform $ paver update_assets lms --settings=aws --themes craftacademy
    ```

    **Notes**: compilation is only needed if changes were made to the stylesheets. Changes to the template files will reflect immediately

5. Restart the app (if new styles were compiled) - Do this as `deploy`

    If you're still logged in as `edxapp` you can exit with `ctrl-d` then restart the app with the following command

    ```bash
    sudo /edx/bin/supervisorctl restart edxapp:
    ```
