Installing AWX
*********************

Pre-Req
###################

.. code-block:: console

    curl -sfL https://get.k3s.io | sh
    dnf -y install git make jq
    cd /etc/yum.repo.d 
    wget https://download.docker.com/linux/centos/docker-ce.repo 
    vi docker.repo  
        At the end of each section add the following:  
        sslverify=0

Starting AWX Operator
###########################

getting the repo
-----------------------

.. code-block:: console
    
    git clone https://github.com/ansible/awx-operator.git
    cd awx-operator 

Setup namespace
----------------------

.. code-block:: console

    export NAMESPACE=awx 
    kubectl create ns ${NAMESPACE} 
    kubectl config set-context --current --namespace=awx

configuring repo
------------------------

.. code-block:: console

    RELEASE_TAG=`curl –s https://api.github.com/repos/ansible/awx-operator/releases/latest | grep tag_name | cut –d ‘”’ -f 4` 
    git checkout $RELEASE_TAG 
    make deploy 
    kubectl get pods –n awx

Edit awx files
-----------------------

You will need to create the following files:

* awx-demo.yml
* awx-ingress.yml
* awx.yml

You should be able to find it via the files section of awx.

Start Kubernetes Cluster
-----------------------------

.. code-block:: console

    kubectl apply -f awx-demo.yml -n awx; kubectl apply -f awx-ingress.yml -n awx; kubectl apply -f awx.yml -n awx

Get admin user default password
-------------------------------------

.. code-block:: console
    
    kubectl get secret awx-demo-admin-password –o jsonpath=”{.data.password}” | base64 –decode 







