Gitag
=====

Automated git version tagging using common format of major.minor.bugfix.build  
  
I was looking for an automated way to annotate my commits with version information and sync git tags as well, resulting
in this little project I call Gitag.

So how does it work?  Good question, but first let me share how it's setup:

Simple -  it consists of two files, one a shell script and the other a config file. The shell script
is placed under the repo's `.git/hook` directory and must be named `post-commit`. The config file is set to go under
the path `.git/tags-config` in the same repo and is named `tags.config`.
  
The `tags.config` file stores values for the following variables:
* major
* minor
* bugfix
* build
* iteration
  
All values are numbers and are set to 0 to start. 
  
Ok, now onto how it works and how to use it.

Simply work as you normal do with git. When composing your commit message unless its a new major, minor or bugfix release
do nothing different.  After commiting git will automatically version your commit as version v0.0.0.1 indicating that it's
build 1 of this project. This version information along with your username will be added to your provided commit message
which other than getting a verison prefix with your username is left alone as originally entered by you.

In addition. a new tag is created for this commit using the same verison number and the tag is pushed to both your repo's
origin and a remote repo called `upstream`. This means that in addition to having version and user info prefixed on the 
commit message you also will have local tags and origin and remote tags in Github for example.
  
To have the system increment any of the other values in your version control information simply include any of the following
keywords in your commit message:

* major
* minor
* bugfix

When the system sees any of these keywords in your commit message it will increment the value for the keyword(s) provided.
Note. if major keyword is provided the system will increment the major value and reset both minor and bugfix to zero.

===
#Author
Lee Cardona  
http://leecardona.com

#Copyright and license
Copyright 2013

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this work except in compliance with the License. You may obtain a copy of the License in the LICENSE file, or at:

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
