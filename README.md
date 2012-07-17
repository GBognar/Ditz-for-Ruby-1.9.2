#ditz 0.5 for Ruby 1.9.x (using 'syck' instead of 'psych')

##Origin
The [original ditz](http://gitorious.org/projects/ditz) project was [forked](https://github.com/chriskempson/Ditz-for-Ruby-1.9.2)
by [chriskempson](https://github.com/chriskempson) to add 'a few tweaks for Ruby 1.9.2'.

##Issues with the Original Version

* With Ruby 1.9.x (including 1.9.3-p194) ditz breaks in Ditz::Model#save! with a 'stack level too deep' message, even if ulimit is unlimited. This happens when using Psych as the YAML engine. 
* When calling ditz with an existing but empty ditz config file, ditz breaks, as Ditz::Model raises a Ditz::ModelError, but the begin...rescue construct handles only the SystemCallError.
* bin/ditz uses the '#!/Users/Chris/.rvm...' line at the top which might not work in general.

##Patches
The patches correcting the above problems are on the 'use-syck' branch of the repository.


(The remaining content below is directly from [chriskempson's fork](https://github.com/chriskempson/Ditz-for-Ruby-1.9.2))

-----

# Ditz 0.5 for Ruby 1.9.2
Ditz stopped working when I upgraded to Ruby 1.9.2 so I'm currently working on bringing it up to scratch for 1.9.2.

## Installation
Make sure you have the `yaml_waml` gem installed. Clone the git repo.
    
    gem install yaml_waml
    git clone git://github.com/ChrisKempson/Ditz-for-Ruby-1.9.2.git
    cd Ditz-for-Ruby-1.9.2
    ruby setup.rb
    ditz --version

## Issues
Ditz is currently falling over if there isn't a release set. This can be fixed by adding a release
    
    ditz add-release
