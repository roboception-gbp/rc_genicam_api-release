2.3.4 (2020-03-15)
------------------

- Workaround for Baumer GenTL GEV interface enumeration bug

2.3.3 (2020-03-06)
------------------

- fix version in package.xml
- fix Dockerfile

2.3.2 (2020-03-06)
------------------

- add libpng-dev dependency in package.xml

2.3.1 (2020-01-10)
------------------

- Reporting full name of stored images, including suffix

2.3.0 (2019-12-20)
------------------

- Tool gc_stream:
  * now also stores the exposure time and gain in parameter files
  * added storing 16 bit images
  * Added parameter '-f png' for storing images in PNG format
  * Reporting all stored images (IntensityRight was missing)
- Tool gc_info:
  * print User defined name
- Refactoring:
  * Moved functions to store images from gc_stream tool into core library
  * Moved function to store point cloud from tool to library
- Fixed:
  * Do not return device if it can be found on different producers
  * reporting device name instead of test option when misspelling the device in 'gc_stream -t <device> ...' call
  * net_perf_check.sh: fix getting mtu

2.2.3 (2019-07-25)
------------------

- Fixed Windows install issues
- Fixing segfault in Buffer::getTLType()

2.2.2 (2019-06-25)
------------------

- Set TLParamsLocked before requesting maximum buffer size
- Only free as many buffers as allocated to avoid errors off GenTL producer
- Request global buffer YPadding only for none multipart buffers to avoid errors of GenTL producer

2.2.1 (2019-06-11)
------------------

- Automatically splitting the stereo images in rc_visards special combined format into Intenstiy and IntensityRight images
- Using TLParamsLocked correctly in streaming class as some cameras require this
- gc_stream now disables component Intensity if IntensityCombined is enabled
- gc_stream now creates parameter file for each Intensity image as well
- Increased timeout for updating the device list to 100 ms as 10 ms can be too less for some cameras / producers

2.2.0 (2019-05-02)
------------------

- gc_info does not report not implemented parameters any more
- gc_info can now also only print specified nodes (which can be a category) by appending the node name with '?' to the device id.
- gc_stream can now measure frequency and latency of incomming buffers
- Windows: look for transport layer in folder of rc_genicam_api.dll
- support modern cmake
  - A "meta target" for all Genicam targets is defined, rc_genicam_api::genicam, on which rc_genicam_api::rc_genicam_api depends publicly.
  - Compile options and definitions of rc_genicam_api are set to private, only /DGENICAM_NO_AUTO_IMPLIB is public
  - Install paths are defined using GNUInstallDirs
- update Baumer GenTL providers to 2.9.2.22969
  - Support for payload type Multi-part added
  - The GigE Producer now find devices connected to virtual interfaces for Linux

2.1.2 (2019-03-13)
------------------

- Remove global include_directories in cmake build files
- Use full precision timestamp in name of images saved by gc_stream
- Append out1 and out2 state to name of images saved by gc_stream

2.1.1 (2019-02-21)
------------------

- Command line tools now exit with != 0 in case of an error
- Improved cmake project files

2.1.0 (2019-01-25)
------------------

- Made System, Interface, Device and Stream objects thread safe

2.0.4 (2019-01-24)
------------------

- A buffer that is labelled to contain chunk data may also contain an image
- Implemented fallback of open device access from readonly to control to exclusive

2.0.3 (2019-01-09)
------------------

- Improved description of some device methods
- Under Windows, do not check install path but only current directory as default location of GenTL producer

2.0.2 (2019-01-01)
------------------

- Fixed bug in rcg::getEnum() function that may lead to a seg fault
- Minor changes in cmake build files

2.0.1 (2018-12-21)
------------------

- Added test mode to gc_stream tool (i.e. disables saving for only testing the connection)
- Added printing of package size to gc_stream tool
- Added statistic to gc_stream tool
- Removed aborting gc_stream with 'Enter' from Linux version as it causes unwanted stops in some situations
- Minor fixes in build files.

2.0.0 (2018-10-08)
------------------

NOTE: Including multipart support required minor changes of the existing API. See readme for more
information. Attention: The provided GenTL layer does not yet support multipart!

- Extended Buffer and Image classes as well as the examples for handling multi-part buffers as well
  (NOTE: The provided GenTL producer does not yet support multipart!)
- gc_stream: Using component name for storing individual images and ensuring that files are not
  overwritten
- gc_pointcloud: Using component name for identifying images and try enabling synchronization on
  device
- Add libs of GenICam reference implementation to external cmake dependencies of shared
  genicam_api library
- Upgrading GenICam reference implementation to v3.1
- Add libs of GenICam reference implementation to external dependencies of shared genicam_api
  library

1.3.15 (2018-09-27)
-------------------

- Added parameter --iponly to gc_config tool

1.3.14 (2018-09-26)
-------------------

- Added possibility to interrupt streaming with gc_stream by pressing 'Enter' key.
- Undefined min/max macros in gc_pointcloud.cc on Windows to avoid compile errors

1.3.13 (2018-08-23)
-------------------

- Changed output of gc_config -l to emphasize using interface and serial number as unique identifier
- Added possibility to call a GenICam command from the command line with gc_info, gc_config and gc_stream
- Additionally printing the internal name and display name of the GenTL producer in the gc_info tool
- Update GEV GenTL provider from Baumer
- Revision of readme

1.3.12 (2018-07-18)
-------------------

- Getting chunk data in gc_stream and storing disparity image with all parameters for reconstruction if possible
- Error handling in gc_stream changed by first checking for incomplete buffer and then for image present

1.3.11 (2018-07-02)
-------------------

- don't install bash completion by default (doesn't work on ROS buildfarm)
- make sure installed net_perf_check.sh script is executable

1.3.10 (2018-06-28)
-------------------

- Added possibility to set GenICam parameters in gc_info too
- Only show network summary in gc_config if called without parameters or with network related parameters
- Corrected spelling of visard in gc_pointcloud output file name

1.3.9 (2018-06-15)
------------------

- Bash completion for UNIX and ROS
- Relaxed synchronization in gc_pointcloud for special exposure alternate mode of rc_visard
- Added method in image list class to request the oldest timestamp
- Added triangulation to gc_pointcloud
- Added parameter for output file name to gc_pointcloud
- Fixed crashing of gc_info if enumeration does not have a value

1.3.8 (2018-04-18)
------------------

- show actually searched path instead of env var in exception if no transport layer found
- improved README

1.3.7 (2018-04-09)
------------------

- Devices can now be discovered by serial number as well

1.3.6 (2018-02-25)
------------------

- fix path to genicam arm64 libs

1.3.5 (2018-02-25)
------------------

- add libs for arm64

1.3.4 (2018-02-23)
------------------

- fix catkin dependency in package.xml

1.3.3 (2018-02-23)
------------------

- fix version in package.xml

1.3.2 (2018-02-23)
------------------

- fix installation of exported targets
- add package.xml for releaseing as ROS third-party package
- update Baumer GigE vision driver to v2.8.15736
- fix architecture detection (use compiler info instead of host kernel)

1.3.1 (2017-12-20)
------------------

- Improved readme
- Porting package to Windows 32 and 64. It can be compiled with Visual Studio.

1.3.0 (2017-12-05)
------------------

New tools / examples:

- Added tool gc_pointcloud that demonstrates synchroneous streaming and 3D
  reconstruction

Improvements of convenience layer:

- Accept true and false for boolean GenICam values additionally to 1 and 0
- Added option to ignore cache when reading parameter
- Added convenience function getColor()
- Added convience function checkFeature()
- Changing request for timestamp in gc_stream tool
- Fixed finding devices by user defined name

Improvement of help texts and messages:

- Improved help for command line tools
- Improved exception description
- Added printing components with enabled status in gc_stream tool
- Removed output of user name in gc_info as this is not the name that can be
  defined via gc_config -n

Changes of access mode to permit parallel read access:

- Open device in gc_info readonly so that it can be used in parallel to an
  open device
- Open device in gc_config readonly if no parameter changes are requested
- Opening device in gc_stream with access mode control
- Changed getDevice() function so that exclusively opened devices are
  discovered as well

Configuration and optimization:

- [baumer] increase NextResendWaitPackets to 200
- add net_perf_check.sh script

Changes in build configuration:

- Ensure that the install directory lib/rc_genicam_api is accessible for
  everybody
- option to disable building of tools
- option for building shared libs
- generate version info
- add option to disable doc target
- Switched off vectorization and looking for CUDA as it is not necessary
- add Baumer GenTL lib for armv7l

1.2.0 (2017-08-15)
------------------

- rename rcgcapi to rc_genicam_api
- getDevice() now accepts specification if interface as prefix
- Added possibility to clean all resources before exit to avoid crashes of GenTL
- add all GenICam files/libs instead of depending on external package
- rename pfnc.h to pixel_formats.h
- bundle GenTL lib from Baumer as fallback if GENICAM_GENTL64_PATH is not set

1.1.5 (2017-05-11)
------------------

- Enforced using IPv4 format for setting persistent IPs and improved output of gc_config

1.1.4 (2017-04-13)
------------------

- Check if device name is not empty before looking for the device
- Fixed formating of MAC addresses as string

1.1.3 (2017-04-11)
------------------

- Catching exceptions in destructors of Device and Stream
- Added changing of GenICam parameters through gc_config

1.1.2 (2017-04-10)
------------------

- Streaming with at least 8 buffers by default
- Additionally show display name when listing devices with gc_config -l

1.1.1 (2017-03-06)
------------------

- Fixed bug in YCbCr411 to RGB conversion

1.1.0 (2017-03-05)
------------------

- Check in gc_stream if buffer is incomplete
- Added optional storing of XML file via gc_info tool
- Added switching PTP on and off via gc_config tool
- Convertions GenApi exceptions to standard exceptions when requesting the node map
- Added helper functions for conversion from YCbCr411 to RGB
- Catching GenApi exception in gc_info tool
- gc_stream tool chooses name of saved images according to pixel format
- Added pfnc.h with custom image format Error8
- Added image and image list helper classes for time synchronization of images
- Open transport layer libraries with deep bind option to prefer local symbol resolution
- Wrapping GenApi Exceptions in get/set feature value helper functions
- Ensure that Buffer::getTimestampNS() always returns a valid value
- Added helper functions for setting and getting features via GenICam
- Fixed crash of gc_stream if device is unknown
- Implemented image streaming and an example for streaming images to file

1.0.1 (2017-02-16)
------------------

- Initial release
