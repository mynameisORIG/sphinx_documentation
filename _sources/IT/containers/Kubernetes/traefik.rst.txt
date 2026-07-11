traefik information
**********************

Edit traefik
###############

.. code-block:: console

    kubectl edit deployment traefik -n kube-system


restart traefik
#######################

.. code-block:: console

    kubectl rollout restart deployment/traefik -n kube-system

check logs
#######################

.. code-block:: console

    kubectl logs -n kube-system deployment/traefik
