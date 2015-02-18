overall:
  To run this script, Administrator(for Windows)/root(for Mac) permission is required

Install:
	silent_install.{bat|sh} [-m size] [-log log_full_path]
    -m: memory size (in MB). if not specified, use default size.
    -log: the full path of the log file. if not specified, use default log path.
          default log path in Windows: ./haxm_silent_run.log
          default log path in Mac: /tmp/haxm_silent_run.log
	In case of success:
		Windows will print "success" while Mac will print nothing. This is to be compliant with Windows/Mac shell convention.
		Return 0 to caller
	In case of fail:
		Print "install failed, please check log <log path> for detail"
		Return 1 to caller

Uninstall:
	silent_install.{bat|sh} -u [-log log_full_path]
      -log: the full path of the log file. if not specified, use default log path.
          default log path in Windows: .\haxm_silent_run.log
          default log path in Mac: /tmp/haxm_silent_run.log
	In case of success:
		Windows will print "success" while Mac will print nothing. This is to be compliant with Windows/Mac shell convention.
		Return 0 to caller
	In case of fail:
		Print "uninstall failed, please check log <log path> for detail"
		Return 1 to caller
	In case of haxm not installed:
		Print "haxm has already been uninstalled"
		Return 0 to caller

Misc
	silent_install.{bat|sh} -v
		If haxm is installed:
			Print haxm version.
			Return 0 to caller
		If haxm is not installed:
			print "HAXM is not installed"
			Return 1 to caller
		
	silent_install.{bat|sh} -c
		Check VT/NX capability of the platform
		Print following message:
			VT support -- yes|no
			NX support -- yes|no
		Return 0 to caller if both VT/NX are supported
		Return 1 to caller if either VT/NX is not supported.
	
	silent_install.{bat|sh} -h
		Print usage
		Return 0 to caller
	
	Wrong parameters:
		Print "wrong parameter. Use -h to show the usage"
		Return 1 to caller
	
known issues:
  1. XD/VT check with "-c" option will only show the CPU capability. it cannot tell if XD/VT is disabled by BIOS
  2. Upgrade to new version is not supported. If you install newer haxm with silent install, you will get "HAXM is already installed".
     But it is ok if you use GUI to do upgrade.
     if you want to do upgrade with silent install script, please do it by uninstall and install.	
