# Check system backup status
sudo systemctl status timeshift
ls -lh /timeshift/snapshots/

# Check disk usage before backup planning
df -h
du -sh ~/Documents/Labs/

# Check last system changes
sudo journalctl --since "24 hours ago" | grep -i "install\|update\|remove"