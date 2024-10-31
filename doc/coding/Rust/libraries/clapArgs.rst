Arguments in CLI using Rust
*******************************

Arguments
################

Make sure to use this library so you can add Arguments

.. code-block:: console

    use clap::{Args, Parser};

This is the final result for Arguments

.. code-block:: console
    struct CommandArgs {
        /// Path to the JSON file
        #[arg(short, long)]
        file: String,

        /// Hostname to search for
        #[arg(short = 'N', long)]
        hostname: String,
    }