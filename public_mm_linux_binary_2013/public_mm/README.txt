*Title: Installing and Running the Public Version of MetaMap
*Author: Willie Rogers

*TOC

* Introduction

MetaMap is a highly configurable program that maps biomedical text to
concepts in the UMLS Metathesaurus
[Note: MetaMap: Mapping Text to the UMLS Metathesaurus, July 2006, http://skr.nlm.nih.gov/papers/references/metamap06.pdf].
This guide is designed to help install MetaMap on the Linux operating system.

* Prerequisites

** MetaMap Terms and Conditions and UMLS License

_Important_: Users are responsible for compliance with the 
[MetaMap Terms and Conditions (http://metamap.nlm.nih.gov/MMTnCs.shtml)].

To use this application, you must have signed 
[the UMLS agreement (http://wwwcf.nlm.nih.gov/umlslicense/snomed/license.cfm)].
The UMLS agreement requires those who use the 
[UMLS (http://www.nlm.nih.gov/research/umls/)] to file a brief
report once a year to summarize their use of the UMLS. It also
requires the acknowledgment that the UMLS contains copyrighted
material and that those copyright restrictions be respected. The UMLS
agreement requires users to agree to obtain agreements for EACH
copyrighted source prior to it's use within a commercial or production
application.

To download MetaMap, you must have access to an UTS account. For
information on how to acquire an UTS account, please see the 
[UMLS Terminology Services Page (http://uts.nlm.nih.gov/)].

** Platform Prerequisites

	[Sun Java Runtime Environment (JRE)] Oracle/Sun's Java 1.6 or
         later is required for use of the SKR-MedPost Part-of-Speech
         (POS) Tagger Server which is required to use MetaMap and the
         Word Sense Disambiguation (WSD) Server which is necessary to
         use the WSD option when running MetaMap.  The JRE is
         available from http://java.com/ .

#--- Note: If you don't plan on using the WSD Server, you can also use the
#--- GNU Compiler for the Java Programming Language (GCJ) for the
#--- SKR-MedPost Tagger Server.  (The Tagger Server has been tested using
#--- GCJ 3.4.6, newer versions should work as well.)  Many Linux
#--- distributions provide pre-compiled packages for GCJ, including Red
#--- Hat, Debian, and Ubuntu.  GCJ is available from the Free Software
#--- Foundation at [http://gcc.gnu.org/java.]

** Space Requirements

MetaMap requires a minimum of 8GB of space to run.

* Getting the distribution

The public distribution can be downloaded at:

  http://metamap.nlm.nih.gov/

#--- For hosts which have access to the CGSB file servers, it is also
#--- available at file:///nfsvol/nlsaux15/public_mm_dist/stage/archive/public__mm__{os}__{year}.tar.bz2

* Extracting the distribution

Use the following |tar| command extract the distribution:

^<<
% tar xvfj public_mm_{os}_{year}.tar.bz2
^>>

|Tar| will create the distribution directory |public_mm|.

* Install

#--- Note: Due to an error creating the distribution the
#--- file |public_mm/.installrc| should removed from the distribution
#--- directory before starting the install process.

** Step 1

To begin the initial install, go to the directory created when you
extracted the distribution (|public_mm|).  You can speed up the
process by telling the install program where your java installation is
by setting the environment variable JAVA_HOME to the Java installation
directory.  If you don't set the variable the program will prompt you
for the information.

To file out where your java installation is located type of the
command line:

^<<
% which java
^>>

To set the environment variable JAVA_HOME:

If the command: |which java| returns /usr/local/jre1.4.2/bin/java,
then JAVA_HOME should be set to /usr/local/jre1.4.2/.

For example:

^<<
# in C Shell (csh or tcsh)
setenv JAVA_HOME /usr/local/jre1.4.2

# in Bourne Again Shell (bash)
export JAVA_HOME=/usr/local/jre1.4.2

# Bourne Shell (sh)
JAVA_HOME=/usr/local/jre1.4.2
export JAVA_HOME
^>>

You also need to add the public_mm/bin directory to your
program path:

^<<
# in C Shell (csh or tcsh)
set path = ( $path <public_mm's parent dir>/public_mm/bin )

# in Bourne Again Shell (bash)
export PATH=$PATH:<public_mm's parent dir>/public_mm/bin

# Bourne Shell (sh)
PATH=$PATH:<public_mm's parent dir>/public_mm/bin
export PATH
^>>


** Step 2

Run the installation script as follows:

^<<
% cd public_mm
% ./bin/install.sh
^>>

An example of a successful installation looks as follows:

^<<
$ cd /nfsvol/nlsaux15/public_mm
$ bin/install.sh 
1
1
Enter basedir of installation [/nfsvol/nlsaux15/public_mm] 

Basedir is set to /nfsvol/nlsaux15/public_mm.

The WSD Server requires Sun's Java Runtime Environment (JRE);
Sun's Java Developer Kit (JDK) will work as well. if the
command: "which" java returns /usr/local/jre1.4.2/bin/java, then the
JRE resides in /usr/local/jre1.4.2/.

Where does your distribution of Sun\'s JRE reside?
Enter home path of JRE (JDK) [/usr/local/jdk1.6.0_11]: 

Using /usr/local/jdk1.6.0_11 for JAVA_HOME.

/nfsvol/nlsaux15/public_mm/WSD_Server/config/disambServer.cfg generated
/nfsvol/nlsaux15/public_mm/WSD_Server/config/log4j.properties generated
Setting up bin directory scripts:
/nfsvol/nlsaux15/public_mm/bin/BuildDataFiles generated.
/nfsvol/nlsaux15/public_mm/bin/builddatafiles.sh generated.
/nfsvol/nlsaux15/public_mm/bin/dfbuilder.profile generated.
/nfsvol/nlsaux15/public_mm/bin/filter_mrconso generated.
/nfsvol/nlsaux15/public_mm/bin/form_opt generated.
/nfsvol/nlsaux15/public_mm/bin/linkSICStus generated.
/nfsvol/nlsaux15/public_mm/bin/LoadDataFiles generated.
/nfsvol/nlsaux15/public_mm/bin/loaddatafiles.sh generated.
/nfsvol/nlsaux15/public_mm/bin/make_all generated.
/nfsvol/nlsaux15/public_mm/bin/metamap{version} generated.
/nfsvol/nlsaux15/public_mm/bin/metamap20{version}.TEMPLATE generated.
/nfsvol/nlsaux15/public_mm/bin/mmserver{version} generated.
/nfsvol/nlsaux15/public_mm/bin/rundatafiles.sh generated.
/nfsvol/nlsaux15/public_mm/bin/SKRenv.{version} generated.
/nfsvol/nlsaux15/public_mm/bin/skrmedpostctl generated.
/nfsvol/nlsaux15/public_mm/bin/SKRrun.{version} generated.
/nfsvol/nlsaux15/public_mm/bin/testapi.sh generated.
/nfsvol/nlsaux15/public_mm/bin/wsdserverctl generated.
Setting up test suite:
/nfsvol/nlsaux15/public_mm/TestSuite/runTest_2011.sh generated.
Checking for required datafiles
Checking for optional datafiles (WSD)
Public MetaMap Install complete.
Public MetaMap Install Settings:

Public MetaMap basedir: /nfsvol/nlsaux15/public_mm
Public MetaMap Program Dir: /nfsvol/nlsaux15/public_mm/bin
Java Home dir: /usr/local/jdk1.6.0_11

$ 
^>>


* Starting MetaMap

MetaMap requires the starting of two servers, The Part-of-Speech
Tagger and Word Sense Disambiguation (WSD) Servers.  They can be
started and stopped as follows:


** Starting the MetaMap Servers


Before running MetaMap you need to start the Tagger and WSD servers.
Both servers will automatically run in the background when started.

	[1. The SKR/Medpost Part-of-Speech Tagger Server]

	% ./bin/skrmedpostctl start

	[2. Word Sense Disambiguation (WSD) Server (optional)]

	% ./bin/wsdserverctl start

** Stopping the servers

You can stop the each server by invoking the corresponding script
with the |stop| parameter:

	[1. The SKR/Medpost Part-of-Speech Tagger Server]

	% ./bin/skrmedpostctl stop

	[2. Word Sense Disambiguation (WSD) Server (optional)]

	% ./bin/wsdserverctl stop

** Determining whether the servers are running

You can determine if the server are running by the command:

^<<
% ps ax | grep java
^>>

The output should look something like this:

^<<
16105 pts/0    Sl     0:00 /usr/local/jdk1.6.0_01/bin/java -Xmx2g -Dserver.config...
16158 pts/0    R+     0:00 grep java
21914 pts/0    Sl     0:02 /usr/bin/gij -Djava.version=1.4.2 -Djava.home=/usr/lib/...
%
^>>


** Invoking MetaMap

If there are no errors starting the WSD and Tagger servers then  
MetaMap can be run as follows:

^<<
% ./bin/metamap{version}
^>>

#-- If you're using the pre-release version of MetaMap use the following command:

#-- ^<<
#-- % ./bin/metamap{version} -L 11 -Z 10
#-- ^>>

#--- If you're using the pre-release version of MMServer 11 (MetaMap Server
#--- 11) use the following command:

#--- ^<<
#--- % ./ bin/mmserver{version} -Z 10
#--- ^>>

MetaMap has a plethora of options that are explained elsewhere.
[Note: MetaMap 2009 Usage, http://metamap.nlm.nih.gov/MM09_Usage.shtml]

#--- * Un-installing MetaMap

#--- Before un-installing MetaMap, make sure both of the MetaMap servers
#--- have been stopped (see [Stopping the servers].)

#--- To un-install MetaMap move to the parent directory of your Metamap
#--- installation and run the uninstall program:

#--- ^<<
#--- % cd <parent directory of installation>
#--- % ./public_mm/bin/uninstall.sh 
#--- Do you really want to uninstall MetaMap? [no/yes] yes
#--- Removing Tagger Server
#--- Removing WSD Server
#--- Removing Lexicon
#--- Removing MetaMap Databases
#--- Removing Programs
#--- Removing Base Directory
#--- Removal of MetaMap installation successful.
#--- %
#--- ^>>



* Datafile Builder 

For users who wish to use there own datasets with MetaMap, a datafile
builder suite is now available.  Go to the MetaMap Web Site
(http://metamap.nlm.nih.gov/) for more information.

* Questions

If you have problems then send email to metamap@nlm.nih.gov.


* Using MetaMap

For more information on running MetaMap and its many options, please
see these references:

	1. MetaMap Readme for Linux, http://metamap.nlm.nih.gov/MM09_Readme.shtml
	2. MetaMap 2009 Usage, http://metamap.nlm.nih.gov/MM09_Usage.shtml
	3. Effective Mapping of Biomedical Text to the UMLS Metathesaurus: The MetaMap Program, 2001,
	   http://skr.nlm.nih.gov/papers/references/metamap_01AMIA.pdf
	4. MetaMap: Mapping Text to the UMLS Metathesaurus, July 2006,
	   http://skr.nlm.nih.gov/papers/references/metamap06.pdf
	5. MetaMap Options and Examples, September 2006,
	   http://skr.nlm.nih.gov/papers/references/MetaMap__Examples_06.pdf
