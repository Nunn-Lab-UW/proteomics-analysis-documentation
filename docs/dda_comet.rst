DDA using Comet
===============

This page provides instructions for running the DDA with Comet Nextflow workflow.

Prerequisites
-------------

.. note::
   These are optional, one-time setup steps.

*  If you plan to upload results to Limelight, please :doc:`set up your Limelight credentials <credentials_limelight>`.
*  If you will be downloading data from Panorama, please :doc:`set up your Panorama credentials <credentials_panorama>`.

Workflow Steps
--------------

1. **Connect to the GSIT (Nexus) system**
   Follow the instructions to :doc:`connect via SSH <ssh_access>`.

2. **Create a directory for the analysis**
   Create and move into a new directory for your analysis. For example:

   .. code-block:: bash

      mkdir comet-run
      cd comet-run

3. **Copy configuration files**
   Copy the template files for the workflow into your new directory:

   .. code-block:: bash

      cp /net/maccoss/vol1/maccoss_shared/nextflow/templates/dda/comet.params .
      cp /net/maccoss/vol1/maccoss_shared/nextflow/templates/dda/pipeline.config .

4. **Update** ``comet.params``
   Edit the ``comet.params`` file for your specific analysis. You can find detailed information about Comet parameters at the `Comet documentation <https://comet-ms.sourceforge.net/parameters/parameters_202101/>`_.

5. **Update** ``pipeline.config``
   Edit the ``pipeline.config`` file to set the parameters for the Nextflow workflow itself.

   More information about the Nextflow parameters can be found in the `workflow documentation <https://nf-ms-dda-comet.readthedocs.io/>`_.

6. **Run the workflow**
   Execute the following script to start the workflow:

   .. code-block:: bash

      /net/maccoss/vol1/maccoss_shared/nextflow/scripts/run-nextflow-dda-nunnlab.sh

Editing Files with Nano
~~~~~~~~~~~~~~~~~~~~~~~

A simple way to edit files on the command line is with the `nano` text editor. To edit a file, run:

.. code-block:: bash

   nano <filename>

For example, to edit `comet.params`:

.. code-block:: bash

   nano comet.params

To save your changes and exit, press ``Ctrl + X``, then ``Y`` to confirm, and finally ``Enter``.

Running with tmux
-----------------

It is highly recommended to run long processes like this workflow inside a `tmux` session. `tmux` is a terminal multiplexer that allows you to create persistent terminal sessions. This means your workflow will continue to run even if you get disconnected from the server.

1. **Start a new `tmux` session and run the workflow:**
   This command creates a new session named `nextflow_run` and executes the workflow script inside it.

   .. code-block:: bash

      tmux new -s nextflow_run "bash -c '/net/maccoss/vol1/maccoss_shared/nextflow/scripts/run-nextflow-dda-nunnlab.sh;exec bash'"

2. **Detach from the session:**
   You can safely detach from the session, and your workflow will continue to run. To detach, press ``Ctrl + b`` followed by ``d``.

3. **Reattach to the session:**
   To check on your workflow's progress, you can reattach to the session at any time:

   .. code-block:: bash

      tmux attach -t nextflow_run

4. **Exit the session:**
   Once the workflow is finished, it is important that you exit the tmux session by typing ``exit`` and pressing ``Enter``.

   .. note::
      If you need to re-execute a workflow, be sure to exit the tmux session before starting another one.

Specifying a Cluster Queue
--------------------------

By default, the workflow runs on the ``sage`` cluster queue, which is the general queue for Genome Sciences users. You can specify a different queue using the ``-q`` flag.

Available queues:

* ``sage``: The general GS cluster queue.
* ``pr``: The UW Proteomics Resource queue.

For example, to run the workflow on the ``pr`` queue:

.. code-block:: bash

   /net/maccoss/vol1/maccoss_shared/nextflow/scripts/run-nextflow-dda-nunnlab.sh -q pr
