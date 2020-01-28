# Jupyter-Rstudio-higher-ed
This is a build log for DSC1(Data Science 1) in an Higher-ed environment


## End goal, An Machine Learning server with some security features for internal research faculty members. ##


### 1. Getting an Ubuntu server 19.10 ready ### 
 1.1 Rufus USB installer for ISO image from ubuntu website 
 
 1.2 Boot from USB, select language, location, user account, dns info, select packages needed
 
 1.3 Setting up Static IP. 
 
### 2. Installation of jupyterhub ###

This step will be mainly following this guide down below. 

http://tljh.jupyter.org/en/latest/install/custom-server.html 

### 3. Add R kernel into hub  ### 

https://irkernel.github.io/installation/#linux-panel 
If you are trying to the same thing on a different system, make sure you are selecting the system info correctly. 

### 4. Harden hub ###  
4.1 Enbling HTTPS 

4.2 Enble Ldap communication 

4.3 SSH connection auth files required, no password login is allow

4.4 Mod root password to something complex 

4.5 Isolated Data science users from system applications 

### 5. Install packages required python ### 

Step1, open jupyterhub and login, click new --> terminal 

Step2, issue the command to install packages 

```
sudo -E pip install pandas   (pandas is the name of the python package) 
```

so far, sklearn, numpy, matplotlib, pandas, tensorflow, GYM, pytorch are installed


NOTES: pip is for python2 packages, pip3 is for python3 packages. 
When you see "no module found" on the jupyter, please make sure that you packages are being installed by the correct version of pip. 

### 6. Install packages required R and Rstudio ### 
Step1, for now, login to server from SSH, then issue sudo R

Step2, same as install R packages from windows enviroment 

```
install.packages("fpp2", repos='http://cran.us.r-project.org') 
```

Step3, setting up the R studio server
https://rstudio.com/products/rstudio/download-server/debian-ubuntu/ 

Step4, now you can access your R studio server from your browser 

### 7. Lession learned ###  
7.1 In order to have all the kernels that you may ever wanted, install jupyter in this sequence 
  Jupyter notebook --> all the kernels that you may need for this project, julia, C#, python3, R, etc. --> install Jupyterlab --> install JupterHub --> might be Jupyter IO 

7.2 Letsencrypt for HTTPS is easy, if this project goes well, an offcial cert will be install 

7.3 Timeout on Notebook, active sessions needs to be limited 

7.4 Pip just one of the ways to install the packages for python, Conda (anaconda, is also a great package manager for python)

7.5 Networking monitoring tool nethogs, glances is newly installed, TCPdump shows some unkown hosts are scanning us. 

7.6 Jupyterhub can also be done in kubernetes clusters, with Helm manager for high performance OR docker for lightweight development built. 

### 8. Migrate plan p2v vmware vSphere (mainly for backup and future support) ###
8.1 Boss is requesting an backup plan with this project. 

8.2 This system is current on a old dell desktop machine, intel 4th gen.  

8.3 An idea pop up from my head about windows enviroment, the idea is installing a client on a old XP or win7 machine, then input your 
esxi host information to login, then you should be able to migrate your physical box from there. Lucky windows machines, they can do an 
live transfer.   

8.4 Same thing apply here, we will take the DD command dump whole linux into a file, then import that file to the vmware workstation pro 

8.5 Output that vm as OVF 

8.6 Import that OVF to vSphere

8.6.1 https://www.nakivo.com/blog/vmware-p2v-linux-conversion-comprehensive-walkthrough/ 

8.7 Job Done. 


