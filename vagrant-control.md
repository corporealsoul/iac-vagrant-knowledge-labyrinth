`PS C:\Users\uniqs> vagrant box remove rhel-9point3-untouched`

`PS C:\Users\uniqs> vagrant box remove ubuntu-22point04point3-untouched`

`PS C:\Users\uniqs> vagrant box list`

<br>

`PS C:\Users\uniqs> vagrant package --base rhel-9point3-untouched --output rhel-9point3-untouched.box`

`PS C:\Users\uniqs> vagrant package --base ubuntu-22point04point3-untouched --output ubuntu-22point04point3-untouched.box`

<br>

`PS C:\Users\uniqs> vagrant box add rhel-9point3-untouched 'D:\Server Snaps\The Architect\rhel-9point3-untouched.box'`

`PS C:\Users\uniqs> vagrant box add ubuntu-22point04point3-untouched 'D:\Server Snaps\The Architect\ubuntu-22point04point3-untouched.box'`

<br>

`PS C:\Users\uniqs> vagrant up`

`PS C:\Users\uniqs> vagrant up --provision`

`PS C:\Users\uniqs> vagrant halt`

`PS C:\Users\uniqs> vagrant destroy`

`PS C:\Users\uniqs> vagrant status`

<br>
