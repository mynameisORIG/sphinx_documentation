Rules and Alerts documentation
***************************************

Wazuh alert levels
#####################

.. list-table:: Wazuh alert levels
    :widths: 25 25 50
    :header-rows: 1

    * - Level
      - Description
      - Action Needed?
    * - 0
      -	Ignored event
      -	No alert generated
    * - 1–3
      -	Low-severity (informational)
      - Mostly logs or normal ops
    * - 4–6
      - Medium-severity (suspicious)
      -	May require investigation
    * - 7–9
      -	High-severity (policy violations)
      - Needs attention
    * - 10–15
      -	Very high (attacks/intrusions)
      -	Immediate action