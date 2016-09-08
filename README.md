WSO2 ESB on OpenShift
=========================

``WSO2 ESB``, the backbone of WSO2's integration platform, used by hundreds of customers to integrate across disparate systems.

More information can be found at http://wso2.com/products/enterprise-service-bus/

Running on OpenShift
--------------------

Create an account at http://openshift.redhat.com/

Create a DIY application. If you may add a PostgreSQL cartridge.

    rhc app create esb diy-0.1 postgresql-9.2

Add this upstream ESB quickstart repo

    git rm -r diy .openshift misc README.md
    git remote add upstream -m master https://github.com/myasas/openshift-esb.git
    git pull -s recursive -X theirs upstream master

Push the repo upstream to OpenShift

    git push

Head to your application at:

    http://esb-$yourdomain.rhcloud.com

Default Credentials
-------------------
<table>
<tr><td>Default Admin Username</td><td>admin</td></tr>
<tr><td>Default Admin Password</td><td>admin</td></tr>
</table>

To give your new ESB site a web address of its own, add your desired alias:

    rhc app add-alias -a esb --alias "$whatever.$mydomain.com"

Then add a cname entry in your domain's dns configuration pointing your alias to $whatever-$yourdomain.rhcloud.com.

