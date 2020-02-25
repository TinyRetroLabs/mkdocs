# TinyRetroLabs Compendium Tools

An easy, simple and fast way to create and deploy documentation with Markdown using [MkDocs](https://www.mkdocs.org/) and [Docker](https://www.docker.com/).

## Usage

Mount the folder where your `mkdocs.yml` resides as a volume into `/docs`:

- Start development server on [http://localhost:8000](http://localhost:8000/)

	```bash
	docker run --rm -it -p 8000:8000 -v ${PWD}:/docs tinyretrolabs/mkdocs
	```

- Build documentation

	```bash
	docker run --rm -it -v ${PWD}:/docs tinyretrolabs/mkdocs build
	```

- Deploy documentation to GitHub Pages

	```bash
	docker run --rm -it -v ~/.ssh:/root/.ssh -v ${PWD}:/docs tinyretrolabs/mkdocs gh-deploy 
	```

## License

As with all Docker images, these likely also contain other software which may be under other licenses (such as Bash, etc from the base distribution, along with any direct or indirect dependencies of the primary software being contained).

As for any pre-built image usage, it is the image user's responsibility to ensure that any use of this image complies with any relevant licenses for all software contained within.

