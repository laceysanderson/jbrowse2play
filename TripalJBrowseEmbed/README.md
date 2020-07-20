
To build the image run the following command in this directory (i.e. `TripalJBrowseEmbed`).
```
$ docker build -t="jbrowse2play:tripal-jbrowse-embed" .
```
This may take awhile -be patient!

To run the image:
```
$ docker run -itd -p 8080:80 -p 5432:5432 --name tripalJBrowseEmbed jbrowse2play:tripal-jbrowse-embed
```

You can now access the following locations in your browser:
 - Your Tripal Site: http://localhost:8080
 - Your JBrowse-Web Installation: http://localhost:8080/sites/all/tools/jbrowse2/index.html
 - JBrowse Demo’s running in your container:
    - Grape vs. Peach Synteny: http://localhost:8080/sites/all/tools/jbrowse2/index.html?config=test_data/config_synteny_grape_peach.json
    - Grape vs. Peach Dotplot: http://localhost:8080/sites/all/tools/jbrowse2/index.html?config=test_data/config_dotplot.json
 - Full Demo Configurations running in your container.
    - For the following links, make sure you begin by adding a view using the toolbar at the top (e.g. File > Add > Linear Genome View)
    - Honeybee Demo: http://localhost:8080/sites/all/tools/jbrowse2/index.html?config=test_data/config_honeybee.json
    - Human Demo: http://localhost:8080/sites/all/tools/jbrowse2/index.html?config=test_data/config_demo.json

## JBrowse Configuration

See the official documentation here: [Intro to the JBrowse 2 configuration](http://jbrowse.org/jb2/docs/config_basic). I recommend usage of the command-line tools (installed on this docker) as described here: [JBrowse2 Command line tools](http://jbrowse.org/jb2/docs/cli).
This docker does not configure a default JBrowse instance by design. As such, you will need to configure your own using the following commands:

## JBrowse Usage

See the [official JBrowse2 user guide](http://jbrowse.org/jb2/docs/user_navigation) for information on how to use this new version of the JBrowse genome viewer.

## Container Maintenance

```
### List all the available containers.
$ docker container list --all

CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                    NAMES
87e4334d97f9        tripalJBrowseEmbed        "docker-entrypoint.s…"   26 minutes ago      Up 25 minutes       0.0.0.0:3000->3000/tcp   nervous_mclean

### See currently running containers.
$ docker ps

CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                    NAMES
87e4334d97f9        tripalJBrowseEmbed        "docker-entrypoint.s…"   25 minutes ago      Up 25 minutes       0.0.0.0:3000->3000/tcp   nervous_mclean

### Stop a container.
$ docker container stop 87e4334d97f9

### Restart a container.
$ docker container start 87e4334d97f9

### Remove all stopped containers.
$ docker container prune
```
