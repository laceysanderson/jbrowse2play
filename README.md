# JBrowse2play

Docker containers for playing with JBrowse2 both within the context of Tripal and independantly.

Three dockerfiles are provided for different purposes:
1. JBrowseUse: The simplest image simply provides a place to play with JBrowse2. It contains a JBrowse site initialized using the JBrowse-cli. 
2. JBrowseDev: This image is for development of JBrowse core and includes a clone of the core jbrowse-components.
3. TripalJBrowseEmbed: Includes both a seeded Tripal site (credit: statonlab) and a JBrowse site initialized using the JBrowse-cli.

**All the above dockers contain an Apache Httpd server, nodejs 10.x and the JBrowse Cli-tools. For docker-specific instructions check out the README.**
