
To build the image run the following command in this directory (i.e. `JBrowseDev`).
```
$ docker build -t="jbrowse2play:jbrowse-dev" .
```
This may take awhile -be patient!

To run the image:
```
$ docker run -itd -p 8070:8080 -p 3000:3000 --name devJBrowse jbrowse2play:jbrowse-dev

$ docker exec -it --workdir /var/www/jbrowse-components/packages/jbrowse-web devJBrowse yarn start
```

You can now access the following locations in your browser:
 - Your JBrowse-Web Installation: http://localhost:3000/index.html
 - JBrowse Demo’s running in your container:
    - Grape vs. Peach Synteny: http://localhost:3000/index.html?config=test_data/config_synteny_grape_peach.json
    - Grape vs. Peach Dotplot: http://localhost:3000/index.html?config=test_data/config_dotplot.json
 - Full Demo Configurations running in your container.
    - For the following links, make sure you begin by adding a view using the toolbar at the top (e.g. File > Add > Linear Genome View)
    - Honeybee Demo: http://localhost:3000/index.html?config=test_data/config_honeybee.json
    - Human Demo: http://localhost:3000/index.html?config=test_data/config_demo.json

## JBrowse Configuration

See the official documentation here: [Intro to the JBrowse 2 configuration](http://jbrowse.org/jb2/docs/config_basic). I recommend usage of the command-line tools (installed on this docker) as described here: [JBrowse2 Command line tools](http://jbrowse.org/jb2/docs/cli).
This docker does not configure a default JBrowse instance by design. As such, you will need to configure your own using the following commands:

```
docker exec --workdir /var/www/jbrowse-components/packages/jbrowse-web/public devJBrowse jbrowse add-assembly https://v1.legumefederation.org/data/public/Pisum_sativum/Cameor.gnm1.P4FG/pissa.Cameor.gnm1.P4FG.genome_main.fna.gz --name "Pisum sativum Cameor v1" --alias pissa.Cameor --type bgzipFasta

docker exec --workdir /var/www/jbrowse-components/packages/jbrowse-web/public devJBrowse jbrowse add-track https://v1.legumefederation.org/data/public/Pisum_sativum/Cameor.gnm1.ann1.7SZR/pissa.Cameor.gnm1.ann1.7SZR.gene_models_main.gff3.gz.csi --name="Genes" --trackId=genes --category="Genes"
```

## JBrowse Usage

See the [official JBrowse2 user guide](http://jbrowse.org/jb2/docs/user_navigation) for information on how to use this new version of the JBrowse genome viewer.

## Container Maintenance

```
### List all the available containers.
$ docker container list --all

CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                    NAMES
87e4334d97f9        useJBrowse        "docker-entrypoint.s…"   26 minutes ago      Up 25 minutes       0.0.0.0:3000->3000/tcp   nervous_mclean

### See currently running containers.
$ docker ps

CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                    NAMES
87e4334d97f9        useJBrowse        "docker-entrypoint.s…"   25 minutes ago      Up 25 minutes       0.0.0.0:3000->3000/tcp   nervous_mclean

### Stop a container.
$ docker container stop 87e4334d97f9

### Restart a container.
$ docker container start 87e4334d97f9

### Remove all stopped containers.
$ docker container prune
```
