Files needed for AWX
****************************

awx-demo.yml
####################

.. code-block:: console

    ---
    apiVersion: awx.ansible.com/v1beta1
    kind: AWX
    metadata:
        name: awx-demo
    spec:
        service_type: nodeport

awx-ingress.yml
##########################

.. code-block:: console

    apiVersion: networking.k8s.io/v1
    kind: Ingress
    metadata:
    name: awx-ingress
    namespace: awx
    annotations:
        traefik.ingress.kubernetes.io/ssl-redirect: "true"
        traefik.ingress.kubernetes.io/router.tls: "true"
        traefik.ingress.kubernetes.io/router.entrypoints: "websecure"
    spec:
    ingressClassName: traefik
    tls:
        - hosts:
            - awx.hogwarts.edu
        secretName: awx-hogwarts-edu-secret
    rules:
        - host: tower-east0.hogwarts.edu
          http:
            paths:
              - path: /
                pathType: Prefix
                backend:
                    service:
                        name: awx-demo-service
                        port:
                            number: 80

awx.yml
###############

.. code-block:: console

    kind: Service
    apiVersion: v1
    metadata:
        name: awx-demo-service
        namespace: awx
    spec:
        type: ClusterIP
        ports:
            - name: http
            port: 80
            targetPort: 80
            - name: https
            port: 443
            targetPort: 443
        selector:
            app: awx-demo

