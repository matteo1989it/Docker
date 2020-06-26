FROM etherpad_etherpad
FROM mariadb:10


##################################
#
#COPY settings.json /opt/etherpad/settings.json
#
#ENV
#ENV
#ENV
#ENV
#
#VOLUME /opt/etherpad/var
#EXPOSE 9001
#CMD ["bin/run.sh", "--root"]
#
#
#
#
#
#
#
#
#
#
#
#
###################################




COPY entrypoint.sh /entrypoint.sh


RUN ln -s var/settings.json settings.json

#TODO
#inside settings.json :
#"dbtype" : "mysql",
#"dbSettings" : {
#	"user" : "etherpad"
#	"host" : "mysql"
#	"password" : "etherpad"
#	"charset" : "utf8mb4"	
#	},

EXPOSE 9001
ENTRYPOINT ["/entrypoint.sh"]
CMD ["bin/run.sh", "--root"]
