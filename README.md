# object-detection-rest-audrey
Waiting for build to start...
Picked Git content provider.
Cloning into '/tmp/repo2dockerz1qv79_h'...
HEAD is now at 26e1059 Initial commit
Building conda environment for python=3.7Using PythonBuildPack builder
Building conda environment for python=3.7Building conda environment for python=3.7Step 1/50 : FROM buildpack-deps:bionic
 ---> 72ccd8e28f8d
Step 2/50 : ENV DEBIAN_FRONTEND=noninteractive
 ---> Using cache
 ---> 851488517ff1
Step 3/50 : RUN apt-get -qq update &&     apt-get -qq install --yes --no-install-recommends locales > /dev/null &&     apt-get -qq purge &&     apt-get -qq clean &&     rm -rf /var/lib/apt/lists/*
 ---> Using cache
 ---> 1ccfce94dcd1
Step 4/50 : RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen &&     locale-gen
 ---> Using cache
 ---> e46609cc845a
Step 5/50 : ENV LC_ALL en_US.UTF-8
 ---> Using cache
 ---> ddfd7444f3a2
Step 6/50 : ENV LANG en_US.UTF-8
 ---> Using cache
 ---> 21c58dbb1fd6
Step 7/50 : ENV LANGUAGE en_US.UTF-8
 ---> Using cache
 ---> 8d164271f61b
Step 8/50 : ENV SHELL /bin/bash
 ---> Using cache
 ---> 717bad870cc5
Step 9/50 : ARG NB_USER
 ---> Using cache
 ---> f884aeffd356
Step 10/50 : ARG NB_UID
 ---> Using cache
 ---> 9a82a456250f
Step 11/50 : ENV USER ${NB_USER}
 ---> Using cache
 ---> 33d3b5049d94
Step 12/50 : ENV HOME /home/${NB_USER}
 ---> Using cache
 ---> c7d6d45756ad
Step 13/50 : RUN groupadd         --gid ${NB_UID}         ${NB_USER} &&     useradd         --comment "Default user"         --create-home         --gid ${NB_UID}         --no-log-init --shell /bin/bash         --uid ${NB_UID}         ${NB_USER}
 ---> Using cache
 ---> 7b05f3b7e1c1
Step 14/50 : RUN wget --quiet -O - https://deb.nodesource.com/gpgkey/nodesource.gpg.key |  apt-key add - &&     DISTRO="bionic" &&     echo "deb https://deb.nodesource.com/node_14.x $DISTRO main" >> /etc/apt/sources.list.d/nodesource.list &&     echo "deb-src https://deb.nodesource.com/node_14.x $DISTRO main" >> /etc/apt/sources.list.d/nodesource.list
 ---> Using cache
 ---> fa68171a49b7
Step 15/50 : RUN apt-get -qq update &&     apt-get -qq install --yes --no-install-recommends    less        nodejs        unzip        > /dev/null &&     apt-get -qq purge &&     apt-get -qq clean &&     rm -rf /var/lib/apt/lists/*
 ---> Using cache
 ---> 773a1e1c9370
Step 16/50 : EXPOSE 8888
 ---> Using cache
 ---> 9f46866b8614
Step 17/50 : ENV APP_BASE /srv
 ---> Using cache
 ---> c04450dceafb
Step 18/50 : ENV NPM_DIR ${APP_BASE}/npm
 ---> Using cache
 ---> 79a74ad99db2
Step 19/50 : ENV NPM_CONFIG_GLOBALCONFIG ${NPM_DIR}/npmrc
 ---> Using cache
 ---> 388ef6998eb3
Step 20/50 : ENV CONDA_DIR ${APP_BASE}/conda
 ---> Using cache
 ---> 8e27273ef50d
Step 21/50 : ENV NB_PYTHON_PREFIX ${CONDA_DIR}/envs/notebook
 ---> Using cache
 ---> 50e109f797f2
Step 22/50 : ENV KERNEL_PYTHON_PREFIX ${NB_PYTHON_PREFIX}
 ---> Using cache
 ---> 715905f9f45b
Step 23/50 : ENV PATH ${NB_PYTHON_PREFIX}/bin:${CONDA_DIR}/bin:${NPM_DIR}/bin:${PATH}
 ---> Using cache
 ---> 5aa6bcd326d1
Step 24/50 : COPY --chown=1000:1000 build_script_files/-2fusr-2flib-2fpython3-2e8-2fsite-2dpackages-2frepo2docker-2fbuildpacks-2fconda-2factivate-2dconda-2esh-391af5 /etc/profile.d/activate-conda.sh
 ---> Using cache
 ---> 0228fc7e7200
Step 25/50 : COPY --chown=1000:1000 build_script_files/-2fusr-2flib-2fpython3-2e8-2fsite-2dpackages-2frepo2docker-2fbuildpacks-2fconda-2fenvironment-2epy-2d3-2e7-2efrozen-2eyml-037262 /tmp/environment.yml
 ---> Using cache
 ---> 24a79c23efce
Step 26/50 : COPY --chown=1000:1000 build_script_files/-2fusr-2flib-2fpython3-2e8-2fsite-2dpackages-2frepo2docker-2fbuildpacks-2fconda-2finstall-2dminiforge-2ebash-514214 /tmp/install-miniforge.bash
 ---> Using cache
 ---> 4065a6144f3e
Step 27/50 : RUN mkdir -p ${NPM_DIR} && chown -R ${NB_USER}:${NB_USER} ${NPM_DIR}
 ---> Using cache
 ---> 5316210e16cb
Step 28/50 : USER ${NB_USER}
 ---> Using cache
 ---> 2b8d289a605b
Step 29/50 : RUN npm config --global set prefix ${NPM_DIR}
 ---> Using cache
 ---> b356b15ba43a
Step 30/50 : USER root
 ---> Using cache
 ---> fd098706749e
Step 31/50 : RUN TIMEFORMAT='time: %3R' bash -c 'time /tmp/install-miniforge.bash' && rm /tmp/install-miniforge.bash /tmp/environment.yml
 ---> Using cache
 ---> 73924a7be696
Step 32/50 : ARG REPO_DIR=${HOME}
 ---> Using cache
 ---> d67619704d80
Step 33/50 : ENV REPO_DIR ${REPO_DIR}
 ---> Using cache
 ---> 30bfd0fef56a
Step 34/50 : WORKDIR ${REPO_DIR}
 ---> Using cache
 ---> 390c4685c3a6
Step 35/50 : RUN chown ${NB_USER}:${NB_USER} ${REPO_DIR}
 ---> Using cache
 ---> 8562cb2e4a60
Step 36/50 : ENV PATH ${HOME}/.local/bin:${REPO_DIR}/.local/bin:${PATH}
 ---> Using cache
 ---> 3219a5e62ec6
Step 37/50 : ENV CONDA_DEFAULT_ENV ${KERNEL_PYTHON_PREFIX}
 ---> Using cache
 ---> 59c95dab5a51
Step 38/50 : COPY --chown=1000:1000 src/requirements.txt ${REPO_DIR}/requirements.txt
 ---> 1c6527bc259b
Step 39/50 : USER ${NB_USER}
 ---> Running in be526b4879a6
Removing intermediate container be526b4879a6
 ---> 93c033029987
Step 40/50 : RUN ${KERNEL_PYTHON_PREFIX}/bin/pip install --no-cache-dir -r "requirements.txt"
 ---> Running in 7070adf5cc6e
Ignoring gunicorn: markers 'python_version < "3.5"' don't match your environment
Collecting Flask
  Downloading Flask-1.1.2-py2.py3-none-any.whl (94 kB)
Collecting gunicorn>=20.0.0
  Downloading gunicorn-20.1.0.tar.gz (370 kB)
Requirement already satisfied: setuptools>=3.0 in /srv/conda/envs/notebook/lib/python3.7/site-packages (from gunicorn>=20.0.0->-r requirements.txt (line 3)) (49.6.0.post20210108)
Collecting itsdangerous>=0.24
  Downloading itsdangerous-1.1.0-py2.py3-none-any.whl (16 kB)
Collecting click>=5.1
  Downloading click-7.1.2-py2.py3-none-any.whl (82 kB)
Requirement already satisfied: Jinja2>=2.10.1 in /srv/conda/envs/notebook/lib/python3.7/site-packages (from Flask->-r requirements.txt (line 1)) (2.11.3)
Collecting Werkzeug>=0.15
  Downloading Werkzeug-1.0.1-py2.py3-none-any.whl (298 kB)
Requirement already satisfied: MarkupSafe>=0.23 in /srv/conda/envs/notebook/lib/python3.7/site-packages (from Jinja2>=2.10.1->Flask->-r requirements.txt (line 1)) (1.1.1)
Building wheels for collected packages: gunicorn
  Building wheel for gunicorn (setup.py): started
  Building wheel for gunicorn (setup.py): finished with status 'done'
  Created wheel for gunicorn: filename=gunicorn-20.1.0-py3-none-any.whl size=78917 sha256=730834274e749c75fe08fcb9141564b0ec528958645ee8c81ab7fcb9bdbb3495
  Stored in directory: /tmp/pip-ephem-wheel-cache-t2dwbpnq/wheels/48/64/50/67e9a3524590218acb6a0c0f94038c0d60815866c52a667d57
Successfully built gunicorn
Installing collected packages: Werkzeug, itsdangerous, click, gunicorn, Flask
Successfully installed Flask-1.1.2 Werkzeug-1.0.1 click-7.1.2 gunicorn-20.1.0 itsdangerous-1.1.0
Removing intermediate container 7070adf5cc6e
 ---> 90b53be8c1b3
Step 41/50 : COPY --chown=1000:1000 src/ ${REPO_DIR}
 ---> 3082c48304b8
Step 42/50 : LABEL repo2docker.ref="26e10592d620f1888b735b66bb247b8a9145c399"
 ---> Running in 2e76b2c8105b
Removing intermediate container 2e76b2c8105b
 ---> 637d56a2597a
Step 43/50 : LABEL repo2docker.repo="https://github.com/adrezni/object-detection-rest-audrey"
 ---> Running in 6fc4aa2d6967
Removing intermediate container 6fc4aa2d6967
 ---> 70fb6cf6c911
Step 44/50 : LABEL repo2docker.version="2021.03.0+11.g0eb7260"
 ---> Running in 188fb793a6e4
Removing intermediate container 188fb793a6e4
 ---> 79e0f99024a0
Step 45/50 : USER ${NB_USER}
 ---> Running in 068faedc3039
Removing intermediate container 068faedc3039
 ---> e91aebad9caa
Step 46/50 : ENV PYTHONUNBUFFERED=1
 ---> Running in 40b009868479
Removing intermediate container 40b009868479
 ---> ed03e577cc9b
Step 47/50 : COPY /python3-login /usr/local/bin/python3-login
 ---> 64cbb62e75c0
Step 48/50 : COPY /repo2docker-entrypoint /usr/local/bin/repo2docker-entrypoint
 ---> 327a32022abb
Step 49/50 : ENTRYPOINT ["/usr/local/bin/repo2docker-entrypoint"]
 ---> Running in f5490144f5fb
Removing intermediate container f5490144f5fb
 ---> e9676ccd77e4
Step 50/50 : CMD ["jupyter", "notebook", "--ip", "0.0.0.0"]
 ---> Running in a3b5c34ac7c9
Removing intermediate container a3b5c34ac7c9
 ---> 09fd41f5686b
{"aux": {"ID": "sha256:09fd41f5686b1774fe184ca44ee63f43555cb0169b88a44270f9c718a3afbafc"}}Successfully built 09fd41f5686b
Successfully tagged gcr.io/binderhub-288415/r2d-staging-72d7634-adrezni-2dobject-2ddetection-2drest-2daudrey-95371f:26e10592d620f1888b735b66bb247b8a9145c399
Pushing image
Successfully pushed gcr.io/binderhub-288415/r2d-staging-72d7634-adrezni-2dobject-2ddetection-2drest-2daudrey-95371f:26e10592d620f1888b735b66bb247b8a9145c399Built image, launching...
Launching server...
