Setting up Limelight Credentials
================================

.. note::
   This is an optional step that only needs to be performed once on the system where you are running workflows. You only need to do this if you will be uploading results to Limelight.

To set up your Limelight access key for uploading data, follow these instructions:

1. Log into Limelight at https://limelight.yeastrc.org/.

2. Click on any project, expand **Upload Data**, and click on **Command Line Import Info**.

3. Click the **Show Key** button and copy the key to your clipboard.
   The key is the string of letters and numbers to the right of ``--user-submit-import-key=``. It should look something like this: ``xd7263ddb8177d4xyzd374594b769f751100jj83777``.

4. Then on the GSIT system, run the following command:

   .. code-block:: bash

      nextflow secrets set LIMELIGHT_SUBMIT_UPLOAD_KEY "xxxxxxxxxx"

   .. important::
      Be sure to replace ``xxxxxxxxxx`` with your access key.

Citing and Getting Help
-----------------------

If you use Limelight in your work, please cite the following publication:

   Limelight: An Open, Web-Based Tool for Visualizing, Sharing, and Analyzing Mass Spectrometry Data from DDA Pipelines. Riffle M, Zelter A, Jaschob D, Hoopmann MR, Faivre DA, Moritz RL, Davis TN, MacCoss MJ, Isoherranen N. J Proteome Res. 2025 Apr 4;24(4):1895-1906. doi: 10.1021/acs.jproteome.4c00968.

For questions, comments, or suggestions, you can:

*  Leave an issue on GitHub: https://github.com/yeastrc/limelight-core/issues
*  Join the Slack channel: https://join.slack.com/t/limelight-ms/shared_invite/zt-pdkll4k3-YR5km0ppSrtdlZCJBvgVyQ
*  Email at: limelightms@uw.edu
