#!/bin/bash
#    Auto On Script Copyright (C) 2012  Arpan Chavda
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with this program.  If not, see <http://www.gnu.org/licenses/>.


m=$(zenity --info --title="Auto On Script" --text "Welcome to Auto On Script.You must read cautions in README.txt before you go ahead by pressing OK.");
m=$?;


if [ $m -eq "0" ]; then
{
	ans=$(zenity  --list --title="Wake up Selection Mode"  --text "Select Mode to Wake up your system" --radiolist  --column "Pick" --column "Opinion" TRUE "Stand by" FALSE "Shut Down"); 

	 dcheck=$?;

        if [ $dcheck -ne "0" ]; then
        {
        exit;
        }
        fi

	a="Stand by";
	
	b="Shut Down";
	
	

	if [ "$ans" = "$a" ]; then
	{
		mode="mem";
	}
	fi
	
	 if [ "$ans" = "$b" ]; then
        {
                mode="disk";
        }
        fi
	

	dt=`zenity --calendar --date-format=%Y-%m-%d`;
	
	dcheck=$?;

	if [ $dcheck -ne "0" ]; then
	{
	exit;
	}
	fi

	hr=$(zenity --entry --title="Wake up Hour" --text "Enter hour(24H format)" --entry-text ""); 
	
	dcheck=$?;

        if [ $dcheck -ne "0" ]; then
        {
        exit;
        }
        fi

		
	min=$(zenity --entry --title="Wake up minutes" --text "Enter minutes" --entry-text ""); 
	
	dcheck=$?;

        if [ $dcheck -ne "0" ]; then
        {
        exit;
        }
        fi

		
	scnd=$(zenity --entry --title="Wake up seconds" --text "Enter seconds" --entry-text ""); 

	dcheck=$?;

        if [ $dcheck -ne "0" ]; then
        {
        exit;
        }
        fi

		
	etime=$(date --date="$dt $hr:$min:$scnd" +%s 2>/dev/null);
	
	dcheck=$?;

        if [ $dcheck -ne "0" ]; then
        {
        exit;
        }
        fi

	ftime=$(date +%s);
	
	
	if [ $ftime -gt $etime 2>/dev/null ]; then
  	{
	rep=$(zenity --info --title="Error in date" --text "Error in given time.You may be entered time in past.script is going to close.");
	exit;
	}

	elif [ $hr -gt 23 2> /dev/null ]; then
	{
	rep=$(zenity --info --title="Error in hour" --text "Error in given hour.script is going to close.");
	exit;
	}

	elif [ $min -gt 59 2> /dev/null ]; then
	{
	rep=$(zenity --info --title="Error in minutes" --text "Error in given minutes.script is going to close.");
	exit;
	}

	elif [ $scnd -gt 59 2>/dev/null ]; then
	{
	rep=$(zenity --info --title="Error in seconds" --text "Error in given seconds.script is going to close.");
	exit;
	}

	else
	{
	final=$(zenity --info --title="Warning" --text "Your system is going in $ans mode and will wakeup at $dt $hr:$min:$scnd.Press OK to perform action.");
	
	}
	fi

	fx=$(zenity --info --title="PC is going in $ans" --text "When you press OK. your PC will go in $ans mode and Power On your PC until it wake up. otherwise press Cancle.");

	difftime=`expr $etime - $ftime `;

	if [ $fx -ne "0" 2>/dev/null ]; then
	{
	exit;
	}
	fi

	rtcwake -a -m $mode -s $difftime; 
	
	exit;

	}
else
{
exit;
}
fi
