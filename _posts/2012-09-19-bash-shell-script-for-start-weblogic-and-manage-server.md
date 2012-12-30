---
layout: post
title: "bash, shell script for start weblogic and manage server"
description: ""
category: howto
tags: [weblogic, bash/shell script]
---
{% include JB/setup %}

### bash/shell script

	#!/bin/sh
	DOMAIN_HOME=/u01/Oracle/Middleware/user_projects/domains/wc_domain
	export DOMAIN_HOME
	
	ADMIN_PORT=7001
	SPACES_PORT=8888
	PORTLET_PORT=8889
	COLLABORATION_PORT=8890
	UTILITIES_PORT=8891
	KTC_PORTAL_PORT=9001
	KTC_APP_PORT=9002
	
	# ------------------------------------------------------------------------------------
	admin_num=`netstat -P tcp | grep "$ADMIN_PORT" | grep -v grep |awk 'END{print NR}'`
	if [ $admin_num -gt 0 ] 
	then echo "WebLogic Admin Server Already RUNNING."
	else echo "Starting Weblogic Admin Server..."
	cd $DOMAIN_HOME/bin
	nohup ./startWebLogic.sh > weblogic.out &
	admin_run=`grep -i RUNNING weblogic.out|grep -v grep |awk 'END{print NR}'`
	   while [ $admin_run -eq 0 ]
	   do
	   sleep 5;
	   admin_run=`grep -i RUNNING weblogic.out|grep -v grep |awk 'END{print NR}'`
	   done
	fi
	
	# KTC Portlal
	# ------------------------------------------------------------------------------------
	ktcportal_num=`netstat -P tcp | grep "$KTC_PORTAL_PORT" | grep -v grep |awk 'END{print NR}'`
	if [ $ktcportal_num -gt 0 ] 
	then echo "WC_KTCPortal Server Already RUNNING."
	else echo "Starting WC_KTCPortal Server..."
	cd $DOMAIN_HOME/bin
	nohup ./startManagedWebLogic.sh WC_KTCPortal > ktcportal.out &
	ktcportal_run=`grep -i RUNNING ktcportal.out|grep -v grep |awk 'END{print NR}'`
	   while [ $ktcportal_run -eq 0 ]
	   do
	   sleep 5;
	   ktcportal_run=`grep -i RUNNING ktcportal.out|grep -v grep |awk 'END{print NR}'`
	   done
	fi
	
	# KTC Application
	# ------------------------------------------------------------------------------------
	ktcapp_num=`netstat -P tcp | grep "$KTC_APP_PORT" | grep -v grep |awk 'END{print NR}'`
	if [ $ktcapp_num -gt 0 ] 
	then echo "WC_KTCApp Server Already RUNNING."
	else echo "Starting WC_KTCApp Server..."
	cd $DOMAIN_HOME/bin
	nohup ./startManagedWebLogic.sh WC_KTCApp > ktcapp.out &
	ktcapp_run=`grep -i RUNNING ktcapp.out|grep -v grep |awk 'END{print NR}'`
	   while [ $ktcapp_run -eq 0 ]
	   do
	   sleep 5;
	   ktcapp_run=`grep -i RUNNING ktcapp.out | grep -v grep |awk 'END{print NR}'`
	   done
	fi
	
	# Spaces
	# ------------------------------------------------------------------------------------
	spaces_num=`netstat -P tcp | grep "$SPACES_PORT" | grep -v grep |awk 'END{print NR}'`
	if [ $spaces_num -gt 0 ] 
	then echo "WC_Spaces Server Already RUNNING."
	else echo "Starting WC_Spaces Server..."
	cd $DOMAIN_HOME/bin
	nohup ./startManagedWebLogic.sh WC_Spaces > spaces.out &
	spaces_run=`grep -i RUNNING spaces.out|grep -v grep |awk 'END{print NR}'`
	   while [ $spaces_run -eq 0 ]
	   do
	   sleep 5;
	   spaces_run=`grep -i RUNNING spaces.out|grep -v grep |awk 'END{print NR}'`
	   done
	fi
	
	# Portlet
	# ------------------------------------------------------------------------------------
	portlet_num=`netstat -P tcp | grep "$PORTLET_PORT" | grep -v grep |awk 'END{print NR}'`
	if [ $portlet_num -gt 0 ] 
	then echo "WC_Portlet Server Already RUNNING."
	else echo "Starting WC_Portlet Server..."
	cd $DOMAIN_HOME/bin
	nohup ./startManagedWebLogic.sh WC_Portlet > portlet.out &
	portlet_run=`grep -i RUNNING portlet.out|grep -v grep |awk 'END{print NR}'`
	   while [ $portlet_run -eq 0 ]
	   do
	   sleep 5;
	   portlet_run=`grep -i RUNNING portlet.out|grep -v grep |awk 'END{print NR}'`
	   done
	fi
	
	# Collaboration
	# ------------------------------------------------------------------------------------
	collaboration_num=`netstat -P tcp | grep "$COLLABORATION_PORT" | grep -v grep |awk 'END{print NR}'`
	if [ $collaboration_num -gt 0 ] 
	then echo "WC_Collaboration Server Already RUNNING."
	else echo "Starting WC_Collaboration Server..."
	cd $DOMAIN_HOME/bin
	nohup ./startManagedWebLogic.sh WC_Collaboration > collaboration.out &
	collaboration_run=`grep -i RUNNING collaboration.out | grep -v grep |awk 'END{print NR}'`
	   while [ $collaboration_run -eq 0 ]
	   do
	   sleep 5;
	   collaboration_run=`grep -i RUNNING collaboration.out | grep -v grep |awk 'END{print NR}'`
	   done
	fi
	
	# Utilities
	# ------------------------------------------------------------------------------------
	utilities_num=`netstat -P tcp | grep "$UTILITIES_PORT" | grep -v grep |awk 'END{print NR}'`
	if [ $utilities_num -gt 0 ] 
	then echo "WC_Utilities Server Already RUNNING."
	else echo "Starting WC_Utilities Server..."
	cd $DOMAIN_HOME/bin
	nohup ./startManagedWebLogic.sh WC_Utilities > utilities.out &
	utilities_run=`grep -i RUNNING utilities.out|grep -v grep |awk 'END{print NR}'`
	   while [ $utilities_run -eq 0 ]
	   do
	   sleep 5;
	   utilities_run=`grep -i RUNNING utilities.out|grep -v grep |awk 'END{print NR}'`
	   done
	fi

