DIA Analysis
============

This section covers running DIA analysis workflows using DIA-NN, EncyclopeDIA, and Casacadia with Nextflow on the GS cluster.

Prerequisites
-------------

.. note::
   These are optional, one-time setup steps.

*  If you will be downloading data from Panorama, please :doc:`set up your Panorama credentials <credentials_panorama>`.

Workflow Steps
--------------

1. **Connect to the GSIT (Nexus) system**
   Follow the instructions to :doc:`connect via SSH <ssh_access>`.

2. **Create a directory for the analysis**
   Create and move into a new directory for your analysis. For example:

   .. code-block:: bash

      mkdir dia-run
      cd dia-run

3. **Copy configuration files**
   Copy the template file for the workflow into your new directory:

   .. code-block:: bash

      cp /net/maccoss/vol1/maccoss_shared/nextflow/templates/dia/pipeline.config .

4. **Update** ``pipeline.config``
   Edit the ``pipeline.config`` file to set the parameters for the Nextflow workflow itself. More information about the Nextflow parameters can be found in the `workflow documentation <https://nf-skyline-dia-ms.readthedocs.io/>`_.

5. **Run the workflow**
   Execute the following script to start the workflow:

   .. code-block:: bash

      /net/maccoss/vol1/maccoss_shared/nextflow/scripts/run-nextflow-dia-nunnlab.sh

Editing Files with Nano
~~~~~~~~~~~~~~~~~~~~~~~

A simple way to edit files on the command line is with the `nano` text editor. To edit a file, run:

.. code-block:: bash

   nano <filename>

For example, to edit `pipeline.config`:

.. code-block:: bash

   nano pipeline.config

To save your changes and exit, press ``Ctrl + X``, then ``Y`` to confirm, and finally ``Enter``.

Running with tmux
-----------------

It is highly recommended to run long processes like this workflow inside a `tmux` session. `tmux` is a terminal multiplexer that allows you to create persistent terminal sessions. This means your workflow will continue to run even if you get disconnected from the server.

1. **Start a new `tmux` session and run the workflow:**
   This command creates a new session named `nextflow_run` and executes the workflow script inside it.

   .. code-block:: bash

      tmux new -s nextflow_run "bash -c '/net/maccoss/vol1/maccoss_shared/nextflow/scripts/run-nextflow-dia-nunnlab.sh;exec bash'"

2. **Detach from the session:**
   You can safely detach from the session, and your workflow will continue to run. To detach, press ``Ctrl + b`` followed by ``d``.

3. **Reattach to the session:**
   To check on your workflow's progress, you can reattach to the session at any time:

   .. code-block:: bash

      tmux attach -t nextflow_run

Specifying a Cluster Queue
--------------------------

By default, the workflow runs on the ``sage`` cluster queue, which is the general queue for Genome Sciences users. You can specify a different queue using the ``-q`` flag.

Available queues:

* ``sage``: The general GS cluster queue.
* ``pr``: The UW Proteomics Resource queue.

For example, to run the workflow on the ``pr`` queue:

.. code-block:: bash

   /net/maccoss/vol1/maccoss_shared/nextflow/scripts/run-nextflow-dia-nunnlab.sh -q pr
