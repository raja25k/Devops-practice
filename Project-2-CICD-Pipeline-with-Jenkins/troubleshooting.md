| Issue                                        | Solution                                               |
| -------------------------------------------- | ------------------------------------------------------ |
| Jenkins not accessible on `:8080`            | Check firewall / Security Group rules                  |
| Jenkins user cannot copy to `/var/www/html/` | Add `jenkins` to `sudo` or change permissions          |
| Job says "SUCCESS" but file not copied       | Double-check Jenkins job shell command output          |
| Git repo authentication issues               | Make sure it's a public repo or use credentials plugin |
