Setting up PanoramaWeb Credentials
==================================

.. note::
   This is an optional step that only needs to be performed once on the system where you are running workflows. You only need to do this if you will be downloading or uploading files from/to PanoramaWeb.

To set up your Panorama API key, follow these instructions:

1. After logging into PanoramaWeb, click the user-shaped icon in the top-right next to your username and choose **External Tool Access**.

2. Click **Generate API Key** then **Copy To Clipboard**.

3. Then on the GSIT system, run the following command (this is one line):

   .. code-block:: bash

      /net/maccoss/vol1/maccoss_shared/nextflow/bin/nextflow secrets set PANORAMA_API_KEY "xxxxxxxxxxxxxxxxxxxxxxxx"

   .. important::
      Be sure to replace ``xxxxxxxxxxxxxxxxxxxxxxxx`` with your access key.
