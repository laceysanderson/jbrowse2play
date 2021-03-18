
To build the image run the following command in this directory (i.e. `JBrowseUse`).
```
docker build -t="jbrowse2play:jbrowse-use" .
```
This may take awhile -be patient!

To run the image:
```
docker run -itd -p 5000:5000 --name useJBrowse jbrowse2play:jbrowse-use
```

You can now access the following locations in your browser:
1. Your JBrowse-Web Installation: http://localhost:5000
    - **This will just say "JBrowse has not been configured yet." until you configure it.**

2. JBrowse Demo’s running in your container:
    - **These open a specific view automatically to show you a specific feature.**
    - Grape vs. Peach Synteny: http://localhost:5000?config=test_data/config_synteny_grape_peach.json
    - Grape vs. Peach Dotplot: http://localhost:5000?config=test_data/config_dotplot.json

3. Full Demo Configurations running in your container.
    - **This begins with an EMPTY JBrowse window.**
    - Make sure you **begin by adding a view** using the toolbar at the top (e.g. File > Add > Linear Genome View)
    - Honeybee Demo: http://localhost:5000?config=test_data/config_honeybee.json
    - Human Demo: http://localhost:5000?config=test_data/config_demo.json

## JBrowse Configuration

See the official documentation here: [Intro to the JBrowse 2 configuration](https://jbrowse.org/jb2/docs/config_guide). I recommend usage of the command-line tools (installed on this docker) as described here: [JBrowse2 Command line tools](https://jbrowse.org/jb2/docs/quickstart_cli).
This docker does not configure a default JBrowse instance by design. As such, you will need to configure your own using the following commands:

```
docker exec useJBrowse jbrowse add-assembly https://v1.legumefederation.org/data/public/Pisum_sativum/Cameor.gnm1.P4FG/pissa.Cameor.gnm1.P4FG.genome_main.fna.gz --name "Pisum sativum Cameor v1" --alias pissa.Cameor --type bgzipFasta

docker exec useJBrowse jbrowse add-track https://v1.legumefederation.org/data/public/Pisum_sativum/Cameor.gnm1.ann1.7SZR/pissa.Cameor.gnm1.ann1.7SZR.gene_models_main.gff3.gz.csi --name="Genes" --trackId=genes --category="Genes"
```

NOTE: This container is built using the [Alpine Linux OS](https://alpinelinux.org/). Bash is not currently installed. Thus to investigate the container you can use `docker exec -it useJBrowse /bin/ash`

## JBrowse Usage

See the [official JBrowse2 user guide](https://jbrowse.org/jb2/docs/user_guide) for information on how to use this new version of the JBrowse genome viewer.

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
