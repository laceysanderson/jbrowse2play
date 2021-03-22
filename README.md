# JBrowse2play

Docker containers for playing with JBrowse2 both within the context of Tripal and independantly.

Three dockerfiles are provided for different purposes:
1. JBrowseUse: The simplest image simply provides a place to play with JBrowse2. It contains a JBrowse site initialized using the JBrowse-cli. 
2. JBrowseDev: This image is for development of JBrowse core and includes a clone of the core jbrowse-components.
3. TripalJBrowseEmbed: Includes both a seeded Tripal site (credit: statonlab) and a JBrowse site initialized using the JBrowse-cli.

## Current Status (2021Mar22)

 - JBrowseUse is on the most recent vesion of JBrowse2 (v1.0.4) and is now using Alpine Linux + Node.js 14.16.0 for a secure production environment.
 - JBrowseDev + TripalJBrowseEmbed are behind and need to be re-tested and updated. However, re-building the image should proviude you with a recent version of JBrowse since it uses the cli tools.
 - Working to provide solid images for use so you don't need to build your own.
 - Embedding is a proof of concept model for Tripal JBrowse and is not yet complete.
