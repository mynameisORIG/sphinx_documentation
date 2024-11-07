Basic commands
**************************

get
#########

You can gather a ton of information with get. Some of the services are the following

* service / svc
* pods
* ingress

**NOTE** the `-n`` is used to specify the namespace **NOTE**

services
++++++++++++

Lists the services of kubernetes cluster

.. code-block:: console

    kubectl get svc -n awx

pods
+++++++++++++

Lists all the pods available in the kubernetes cluster

.. code-block:: console

    kubectl get pods -n awx

ingress
+++++++++++

Lists the information about the ingress controller in kubernetes

.. code-block:: console

    kubectl get ingress -n awx

namespace
#############

This helps organization projects. To create one and set as current config, run the following:

.. code-block:: console

    kubectl create ns NAMESPACE
    kubectl config set-context --current --namespace=NAMESPACE

Get pod shell
################

To enter the shell of the pod, run the following:

.. code-block:: console

    kubectl exec -it PODNAME -n NAMESPACE -- /bin/bash