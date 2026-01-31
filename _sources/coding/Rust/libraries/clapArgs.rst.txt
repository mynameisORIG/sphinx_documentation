Arguments in CLI using Rust
*******************************

Arguments
################

Make sure to use this library so you can add Arguments

.. code-block:: console

    use clap::{Args, Parser};

This is the final result for Arguments

.. code-block:: console

    #[derive(Parser, Debug)]
    #[command(name = "Machine Lookup", about = "Find machine details by hostname")]
    struct CommandArgs {
        /// Path to the JSON file
        #[arg(short, long)]
        file: String,

        /// Hostname to search for
        #[arg(short = 'N', long)]
        hostname: String,
    }

This needs to go in the main function. This parses CLI arguments and stores them in the `args` variable

.. code-block:: console

    let args = CommandArgs::parse();