# metamr

Meta-stuff for the MR family.

## Docker images

The images are organized by folder:
  - `circleci_ubuntu-20.04` is the image used to test MRChem and MRCPP 
  - `circleci_ubuntu-18.04` is the older image used to test MRChem and MRCPP 
  - `circleci_ubuntu-18.04-conda` is the image used to test VAMPyR

The image used on CircleCI for testing is built automatically with GitHub actions.
You can download it locally with:

    docker pull ghcr.io/mrchemsoft/metamr/circleci_ubuntu-18.04
    
and then get a shell inside the container with

    docker run -it metamr/circleci_ubuntu18.04
    
This can be useful to troubleshoot CI failures.

We also provide another image to run MRChem directly. You can run it with:

    docker run ghcr.io/mrchemsoft/metamr/mrchem_ubuntu18.04 </path/to/input/file>
