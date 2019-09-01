script=helloWorld.py

run:
	@python 01-example/$(script)

build:
	@python setup.py build

sdist:
	@python setup.py sdist

install: sdist
	@python setup.py install

.PHONY: clean
clean:
	rm -fR build dist *egg-info
