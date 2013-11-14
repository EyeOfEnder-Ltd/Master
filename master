#!/bin/sh
# Master Script

function helpMenu {
    echo ""
    echo "Master - EyeOfEnder server control script."
    echo "    master start <server>      - start a server"
    echo "    master stop <server>       - stop a server"
    echo "    master servers             - lists running servers"
    echo "    master view <server>       - view a server console"
    echo "    master exists <server>     - checks if a server is running"
    echo "    master dist <server>       - distribute /dist/* files to a server"
    echo ""
    echo "~ Made by LimeByte"
    echo ""
}

if [ $1 ]
then
    case "$1" in
    "start")
        if [ $2 ]
        then
            if ! screen -list | grep -q "$2"; then
                cd /root/$2
                screen -dmS $2 ./run.sh
                echo "Server started."
            else
                echo "Server is already running!";
            fi
        else
            echo 'Please specify a server.'
        fi
    ;;
    "stop")
        if [ $2 ]
        then
            if ! screen -list | grep -q "$2"; then
                echo "Server not running!";
            else
                screen -S $2 -X quit
                echo "Server stopped" 
            fi
        else
            echo 'Please specify a server.'
        fi
    ;;
    "servers")
        screen -ls
    ;;
    "view")
        if [ $2 ]
        then
            screen -r $2
        else
            echo 'Please specify a server.'
        fi
    ;;
    "exists")
        if [ $2 ]
        then
            if ! screen -list | grep -q "$2"; then
                echo "Not running.";
            else
                echo "Running.";
            fi
        else
            echo 'Please specify a server.'
        fi
    ;;
    "dist")
        if [ $2 ]
        then
            if ! screen -list | grep -q "$2"; then
                cp -r /root/dist/* /root/$2
                echo "Files distributed.";
            else
                echo "Server must not be running!";
            fi
        else
            echo 'Please specify a server.'
        fi
    ;;
    esac
else
    helpMenu
fi
