## [[Linux]] [[Arch]] [[compress and extract]] [[pacman]]

sudo pacman -Rcns <package>

-R remove
-c cascade / check what will be removed
-n no save
-s remove dependencies

if -c shows some potential problems, then cancel it.

Run                   sudo -Runs <package>
-u avoid removing packages if other packages depend on it.