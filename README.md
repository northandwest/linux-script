# linux-script

#!/bin/bash  
#deploy.sh
#version 2017-10-17 v0.5
if [ $# -eq 0 ]; then
    echo "Param not input."
else
    targetPath=$2
    sourcePath=$1
    fileName=$3
    tomcatAddress=$4
    configPath=$5

    echo "deply $fileName.war at $1. Project:front.ly"

        myFile="$sourcePath/$fileName.war"

        echo "finding war ${myFile} ... ..."

        if [  -f "$myFile" ]; then
　　
        $tomcatAddress/bin/shutdown.sh
        cd $targetPath
        rm -rf *
        unzip $myFile -d ROOT

        cp -rf $configPath .
        $tomcatAddress/bin/startup.sh
        else
                echo "$myFile is not upload!"
        fi

fi

##
#!/bin/bash
if [ $# -eq 0 ]; then
    echo "Name not provided."
else
    echo "deply front.war at $1. Project:front.ly"

        tomcatPath="/opt/software/apache-tomcat-bank-admin"
        sourcePath="/release/bankly/$1"
        targetPath="$tomcatPath/webapps"
        configPath="/config/admin.ly/ROOT"
        projectName="web"

       /root/deploy.sh $sourcePath $targetPath $projectName $tomcatPath $configPath
fi



