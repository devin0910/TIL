sudo apt-get install wireshark
sudo dpkg-reconfigure wireshark-common 
sudo usermod -a -G wireshark $USER
gnome-session-quit --logout --no-prompt
