# 26-add-logic-to-apply-tuxedo-patch

This functionality applies tuxedo patch as listed in `psft_patches.yaml`.  It also fixes the archive extraction logic. As delivered, Oracle uses COM-object model to extract the archive.  Unfortunately, COM-object model doesn't work on Core and embedded systems.  So, instead, we convert the archive extraction to .NET for more universal compatibility.
