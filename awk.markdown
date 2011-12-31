AWK Notes
====

#### Analysis email address in CSDN file using awk

	# get the content after @, which is the email service provider
	awk -F ' # ' '{print tolower(substr($3, index($3, "@")))}' www.csdn.net.sql > csdn_email.txt
	
	# sum total number for each email service provider
	awk '{if(!a[$1]) {a[$1] = 1} else {a[$1]++}} END {for(i in a) {print a[i], i}}' csdn_email.txt > csdn_email_summary.txt 
	
	# sort the result
	sort -r -g csdn_email_summary.txt > csdn_email_summary_ordered.txt