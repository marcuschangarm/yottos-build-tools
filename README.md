yottos-build-tools
==================

Templates for building Debian/Ubuntu packages. Each package contains a DEBIAN folder with the following control files:
```bash
control  - Package manifest. Contains architecture (i386/amd64/all), version, dependencies, etc.
postinst - Script to run after installation.
postrm   - Script to run after removal. 
```

Insert the missing binary files (look for the README files) and build package with:
```bash
dpkg -b <package folder> .
```

Generate repository index from package folder with:
```bash
dpkg-scanpackages <repository folder> | gzip -9c > <repository folder>/Packages.gz
```

Upload repository folder with packages and index to cloud storage. 
Insert in /etc/apt/sources.list the address to the repository:
```bash
deb <URL> <repository folder>/
```
