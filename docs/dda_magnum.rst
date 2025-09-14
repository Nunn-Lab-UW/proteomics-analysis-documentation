Open Modification DDA using Magnum
==================================

This page describes how to run a workflow that uses Magnum and Percolator for open modification DDA proteomics searching and uploading those results to Limelight for visualization, analysis, and sharing.

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

      mkdir magnum-run
      cd magnum-run

3. **Copy configuration files**
   Copy the template files for the workflow into your new directory:

   .. code-block:: bash

      cp /net/maccoss/vol1/maccoss_shared/nextflow/templates/openmod-dda/Magnum.conf .
      cp /net/maccoss/vol1/maccoss_shared/nextflow/templates/openmod-dda/pipeline.config .

4. **Update** ``Magnum.conf``
   Edit the ``Magnum.conf`` file for your specific analysis. You can find detailed information about Magnum parameters at the `Magnum documentation <https://magnum-ms.org/param/index.html>`_.

5. **Update** ``pipeline.config``
   Edit the ``pipeline.config`` file to set the parameters for the Nextflow workflow itself.

6. **Run the workflow**
   Execute the following script to start the workflow:

   .. code-block:: bash

      /net/maccoss/vol1/maccoss_shared/nextflow/scripts/run-nextflow-dda-openmod-nunnlab.sh

Editing Files with Nano
~~~~~~~~~~~~~~~~~~~~~~~

A simple way to edit files on the command line is with the `nano` text editor. To edit a file, run:

.. code-block:: bash

   nano <filename>

For example, to edit `Magnum.conf`:

.. code-block:: bash

   nano Magnum.conf

To save your changes and exit, press ``Ctrl + X``, then ``Y`` to confirm, and finally ``Enter``.

Running with tmux
-----------------

.. note::
   When you connect to ``nexus.gs.washington.edu``, you are randomly logged into one of ``nexus1``, ``nexus2``, or ``nexus3``. To reattach to a ``tmux`` session, you must be logged into the same server where the session is running.

   It is recommended to explicitly connect to a specific server (e.g., ``ssh your_username@nexus1.gs.washington.edu``) to make it easier to find and reattach to your sessions later.

It is highly recommended to run long processes like this workflow inside a `tmux` session. `tmux` is a terminal multiplexer that allows you to create persistent terminal sessions. This means your workflow will continue to run even if you get disconnected from the server.

1. **Start a new `tmux` session and run the workflow:**
   This command creates a new session named `nextflow_run` and executes the workflow script inside it.

   .. code-block:: bash

      tmux new -s nextflow_run "bash -c '/net/maccoss/vol1/maccoss_shared/nextflow/scripts/run-nextflow-dda-openmod-nunnlab.sh;exec bash'"

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

   /net/maccoss/vol1/maccoss_shared/nextflow/scripts/run-nextflow-dda-openmod-nunnlab.sh -q pr
