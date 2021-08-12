

STEP 1 — INSTALLING APACHE AND UPDATING THE FIREWALL

Wednesday, August 11, 2021

3:43 PM

Step1:

First going to spin a server I aws

Make sure Im in the EC2 dashboard, you can use search bar to find it

Screen clipping taken: 8/11/2021 1:04 PM

You are prompted to choose an Machine Image for we are going to use

Ubuntu Server 20.04 LTS (HVM), SSD Volume Type Click **Select**

For this example I have chosen Free tier

Screen clipping taken: 8/11/2021 1:06 PM

We will leave the defaults and Launch it

Screen clipping taken: 8/11/2021 1:10 PM

As you can see we have a Security Group applied to this instance by default that allows us to SSH

After Review you can Launch

Now I will create a key pair, I will need this key to ssh into the instance

Once the key (extension .pèm) is securte Launch the isntance

Go the instnaces view

Screen clipping taken: 8/11/2021 1:32 PM

Will connect to the instance now. To find information on how to connect

Click on "Intance ID"

Bottom Connect

SSH client for instructions





Copy the string under Example: it contains everything you need to connect from your terminal.

• Make sure that when you run this string your current working directory contains .pem pair key, by default it is using a relative path to your this key.

Once you run the string/comands you will get

ssh -i "daro.io.pem" ubuntu@ec2-3-216-90-84.compute-1.amazonaws.com

When I download the key, it downloaded daroio.pem instead of daro.io.pem, changed the name in the command

Ànd I successfully log in to the ubuntu

Install Apache using Ubuntu’s package manager [‘apt’](https://en.wikipedia.org/wiki/APT_\(software\)):

#update a list of packages in package managersudo apt update

#run apache2 package installationsudo apt install apache2

To verify that apache2 is running as a Service in our OS, use following command

sudo systemctl status apache2

I like to do one big cmd

sudo apt update && sudo apt install apache2 -y

systemctl status apache2

Now we need to make sure our page can be access using HTTP. We will apply a security group

Once again navigate o your instnace view, click on instnace ID and Security

òr

Select your instnance

Screen clipping taken: 8/11/2021 2:22 PM

Click on "Security Group"

Might be different for you

This is the security group currently applied to the instance and we are going to add a rule to allow HTTP.

Under Tab "Inbound Rules" click button "Edit Inbound Rules"

We add Rule

The Proctocol or type "HTTP" and source 0.0.0.0/0 meaning all Ips, you can also use DropDown menu "Anywhere-IPv4"

Save it

now we can send http request using a browser

Before

after

Screen clipping taken: 8/11/2021 3:05 PM





Issue getting the page up after add rule might have be due to instead of using the dropdown, you type 0.0.0.0/0 manually and might have had a typo

