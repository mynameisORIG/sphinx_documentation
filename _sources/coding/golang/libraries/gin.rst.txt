Gin library
*************************

What is Gin
#################

Gin is a HTTP web framework written in Go (Golang). It features a Martini-like API, but with performance up to 40 times faster than Martini. If you need smashing performance, get yourself some Gin.
How to use Gin?

Install modules
##########################

.. code-block:: console

    go install github.com/gin-gonic/gin@latest

Code Understanding
#########################

Initalize gin engine
-------------------------------

* The gin.Default() function sets up a default router with common middleware like request logging, error recovery, etc.

.. code-block:: console

    r := gin.Default()

Serve Static Files for React Front End
-----------------------------------------------

.. code-block:: console

    r.Static("/static", "./frontend/build/static")
    r.StaticFile("/", "./frontend/build/index.html")

* `r.Static("/static", "./frontend/build/static")`: This tells Gin to serve static files from the `./frontend/build/static` directory when a client requests files under the `/static` path.
* `r.StaticFile("/", "./frontend/build/index.html")`: This serves the `index.html` file from the React build folder when the root URL (/) is requested. Essentially, it serves the main entry point of the React application.

Define the API endpoint
------------------------------------

.. code-block:: console

    r.GET("/api/run-script", func(c *gin.Context) {
    out, err := exec.Command("bash", "-c", "./test.sh").Output()
    if err != nil {
        c.JSON(http.StatusInternalServerError, gin.H{"error": err.Error()})
        return
    }

    c.JSON(http.StatusOK, gin.H{"output": string(out)})
    })

* r.GET("/api/run-script", ...): This defines a GET endpoint at /api/run-script using Gin's GET method. When a request is made to this endpoint, the associated handler function is executed.
Inside the handler:

 * It runs a shell script (test.sh) using exec.Command.
 * If the script runs successfully, the output is returned to the client in a JSON response.
 * If there is an error running the script, an error message is returned with an HTTP 500 status code.

* Gin’s c.JSON() method is used to send a JSON response back to the client.