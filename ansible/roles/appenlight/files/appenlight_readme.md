# AppEnlight Cheat Sheet


AppEnlight web application admin login/password: admin/admin

Administrator sudo password: `vagrant`

Administrator documentation: https://docs.rhodecode.com/RhodeCode-Appenlight/

User documentation: http://getappenlight.com/page/api/main.html

Controlling AppEnlight processes: 

    sudo systemctl restart appenlight
    sudo systemctl restart appenlight_api
    sudo systemctl restart appenlight_celery
    sudo systemctl restart appenlight_celery_beat
    sudo systemctl restart appenlight_uptime_ce

    journalctl -f -u appenlight
    journalctl -f -u appenlight_api
    journalctl -f -u appenlight_celery
    journalctl -f -u appenlight_celery_beat
    journalctl -f -u appenlight_uptime


# Locations of important config files

Postgresql customization: `/etc/postgresql/XX/main/conf.d/customized.conf`

AppEnlight server: `/home/appenlight/appenlight/production.ini`

AppEnlight uptime script:  `/home/appenlight/appenlight/uptime_config.ini`

