# Challenges and Guidelines in Deep Generative Protein Design

![Static Badge](https://img.shields.io/badge/arXiv-2411.18568-red?link=https%3A%2F%2Fdoi.org%2F10.48550%2FarXiv.2411.18568)

## Protein Structures Data

```
BLDB:   Beta-lactamases
CYTC:   Cytochrom c
GFP:    GFP
Ras:    Ras GTPase
```

Metadata of protein structures used for training can be found in `/data/*.csv`.

### Generated Structures

```
B:      Backbone only
BQ:     Backbone + Optimal predicted sequences
BQS:    Backbone + Optimal preidcted sequences + homology modeled side-chains
BQSH:   Backbone + Optimal preidcted sequences + homology modeled side-chains + hydrogen atoms added
C:      Conserved residues
Q:      Optimal predicted sequences
```

## Dependencies

### Python Packages

<details>
<summary><i>environment</i></summary>

```
  - _libgcc_mutex=0.1=conda_forge
  - _openmp_mutex=4.5=2_gnu
  - alsa-lib=1.2.8=h166bdaf_0
  - argon2-cffi=23.1.0=pyhd8ed1ab_1
  - argon2-cffi-bindings=21.2.0=py310ha75aee5_5
  - argtable2=2.13=hd590300_1004
  - arrow=1.3.0=pyhd8ed1ab_1
  - attr=2.5.1=h166bdaf_1
  - attrs=25.3.0=pyh71513ae_0
  - autodock-vina=1.1.2=h9ee0642_3
  - blas=1.0=openblas
  - bleach-with-css=6.2.0=h82add2a_4
  - blosc=1.21.5=hc2324a3_1
  - bottleneck=1.3.7=py310ha9d4c09_0
  - brotli-bin=1.0.9=h5eee18b_8
  - brotli-python=1.0.9=py310hd8f1fbe_8
  - bzip2=1.0.8=h5eee18b_6
  - c-ares=1.19.1=h5eee18b_0
  - ca-certificates=2025.1.31=hbcca054_0
  - cached-property=1.5.2=hd8ed1ab_1
  - cached_property=1.5.2=pyha770c72_1
  - cairo=1.18.0=h3faef2a_0
  - cffi=1.17.1=py310h8deb56e_0
  - chardet=5.2.0=pyhd8ed1ab_3
  - clustalo=1.2.4=h503566f_9
  - colorama=0.4.6=py310h06a4308_0
  - comm=0.2.2=pyhd8ed1ab_1
  - contourpy=1.2.0=py310hdb19cb5_0
  - curl=8.12.1=h251f7ec_0
  - custom-inherit=2.4.1=pyhd8ed1ab_0
  - cycler=0.11.0=pyhd3eb1b0_0
  - cyrus-sasl=2.1.28=h52b45da_1
  - dbus=1.13.18=hb2f20db_0
  - defusedxml=0.7.1=pyhd8ed1ab_0
  - dendropy=5.0.6=pyhdfd78af_0
  - emboss=6.6.0=hfb8fa87_10
  - ete3=3.1.3=pyhd8ed1ab_0
  - exceptiongroup=1.2.2=pyhd8ed1ab_1
  - executing=2.1.0=pyhd8ed1ab_1
  - expat=2.6.3=h6a678d5_0
  - fasttree=2.1.11=h7b50bb2_5
  - fftw=3.3.10=nompi_hf1063bd_110
  - font-ttf-dejavu-sans-mono=2.37=hab24e00_0
  - font-ttf-inconsolata=3.000=h77eed37_0
  - font-ttf-source-code-pro=2.038=h77eed37_0
  - font-ttf-ubuntu=0.83=h77eed37_3
  - fontconfig=2.14.2=h14ed4e7_0
  - fonts-conda-ecosystem=1=0
  - fonts-conda-forge=1=0
  - fonttools=4.51.0=py310h5eee18b_0
  - fqdn=1.5.1=pyhd8ed1ab_1
  - freetype=2.12.1=h267a509_2
  - freetype-py=2.3.0=pyhd8ed1ab_0
  - future=1.0.0=pyhd8ed1ab_2
  - gettext=0.23.1=h5888daf_0
  - gettext-tools=0.23.1=h5888daf_0
  - glew=2.1.0=h295c915_3
  - glib=2.78.4=hfc55251_0
  - glib-tools=2.78.4=hfc55251_0
  - glm=0.9.9.8=h00ab1b0_0
  - graphite2=1.3.13=h59595ed_1003
  - gst-plugins-base=1.18.4=h29181c9_0
  - gstreamer=1.22.0=h25f0c4b_2
  - gstreamer-orc=0.4.41=h17648ed_0
  - h11=0.14.0=pyhd8ed1ab_1
  - h2=4.2.0=pyhd8ed1ab_0
  - harfbuzz=8.3.0=h3d44ed6_0
  - hdf4=4.2.15=h9772cbc_5
  - hdf5=1.12.2=nompi_h4df4325_101
  - hdf5-1107=1.10.7=0
  - hpack=4.1.0=pyhd8ed1ab_0
  - hyperframe=6.1.0=pyhd8ed1ab_0
  - icu=73.2=h59595ed_0
  - idna=3.10=pyhd8ed1ab_1
  - importlib-metadata=8.6.1=pyha770c72_0
  - importlib_resources=6.5.2=pyhd8ed1ab_0
  - ipykernel=6.29.5=pyh3099207_0
  - ipywidgets=8.1.5=pyhd8ed1ab_1
  - isoduration=20.11.0=pyhd8ed1ab_1
  - jack=1.9.22=h11f4161_0
  - joblib=1.4.2=py310h06a4308_0
  - jpeg=9e=h5eee18b_3
  - jsonpointer=3.0.0=py310hff52083_1
  - jsonschema=4.23.0=pyhd8ed1ab_1
  - jsonschema-specifications=2024.10.1=pyhd8ed1ab_1
  - jsonschema-with-format-nongpl=4.23.0=hd8ed1ab_1
  - jupyter=1.1.1=pyhd8ed1ab_1
  - jupyter-lsp=2.2.5=pyhd8ed1ab_1
  - jupyter_client=8.6.3=pyhd8ed1ab_1
  - jupyter_console=6.6.3=pyhd8ed1ab_1
  - jupyter_core=5.7.2=pyh31011fe_1
  - jupyter_events=0.12.0=pyh29332c3_0
  - jupyter_server=2.15.0=pyhd8ed1ab_0
  - jupyter_server_terminals=0.5.3=pyhd8ed1ab_1
  - jupyterlab=4.3.6=pyhd8ed1ab_0
  - jupyterlab_pygments=0.3.0=pyhd8ed1ab_2
  - jupyterlab_server=2.27.3=pyhd8ed1ab_1
  - jupyterlab_widgets=3.0.13=pyhd8ed1ab_1
  - kiwisolver=1.4.4=py310h6a678d5_0
  - krb5=1.20.1=h143b758_1
  - lame=3.100=h166bdaf_1003
  - lcms2=2.12=h3be6417_0
  - ld_impl_linux-64=2.40=h12ee557_0
  - lerc=3.0=h295c915_0
  - libabseil=20250127.0=cxx17_hbbce691_0
  - libaec=1.1.3=h59595ed_0
  - libasprintf=0.23.1=h8e693c7_0
  - libasprintf-devel=0.23.1=h8e693c7_0
  - libbrotlicommon=1.0.9=h5eee18b_8
  - libbrotlidec=1.0.9=h5eee18b_8
  - libbrotlienc=1.0.9=h5eee18b_8
  - libcap=2.67=he9d0100_0
  - libclang=15.0.7=default_h127d8a8_5
  - libclang13=15.0.7=default_h5d6823c_5
  - libcups=2.3.3=h36d4200_3
  - libcurl=8.12.1=hc9e6f67_0
  - libdb=6.2.32=h9c3ff4c_0
  - libdeflate=1.12=h166bdaf_0
  - libedit=3.1.20230828=h5eee18b_0
  - libev=4.33=h7f8727e_1
  - libevent=2.1.10=h28343ad_4
  - libexpat=2.6.3=h5888daf_0
  - libffi=3.4.4=h6a678d5_1
  - libflac=1.4.3=h59595ed_0
  - libgcc=14.1.0=h77fa898_1
  - libgcc-ng=14.1.0=h69a702a_1
  - libgcrypt=1.11.0=ha770c72_2
  - libgcrypt-devel=1.11.0=hb9d3cd8_2
  - libgcrypt-lib=1.11.0=hb9d3cd8_2
  - libgcrypt-tools=1.11.0=hb9d3cd8_2
  - libgd=2.3.3=h695aa2c_1
  - libgettextpo=0.23.1=h5888daf_0
  - libgettextpo-devel=0.23.1=h5888daf_0
  - libgfortran-ng=8.2.0=hdf63c60_1
  - libgfortran5=14.1.0=hc5f4f2c_1
  - libglib=2.78.4=h783c2da_0
  - libglu=9.0.0=hf484d3e_1
  - libgomp=14.1.0=h77fa898_1
  - libgpg-error=1.51=hbd13f7d_1
  - libharu=2.4.4=h267a509_0
  - libiconv=1.18=h4ce23a2_1
  - libidn2=2.3.8=ha4ef2c3_0
  - libllvm14=14.0.6=hcd5def8_4
  - libllvm15=15.0.7=hadd5161_1
  - libltdl=2.4.3a=h5888daf_0
  - libnetcdf=4.9.1=nompi_h34a3ff0_101
  - libnghttp2=1.57.0=h2d74bed_0
  - libnsl=2.0.1=hd590300_0
  - libogg=1.3.5=h4ab18f5_0
  - libopenblas=0.3.21=h043d6bf_0
  - libopus=1.3.1=h7f98852_1
  - libpng=1.6.43=h2797004_0
  - libpq=17.4=hdbd6064_0
  - libprotobuf=5.29.3=hc99497a_0
  - libsndfile=1.2.2=hc60ed4a_1
  - libsodium=1.0.18=h36c2ea0_1
  - libsqlite=3.45.2=h2797004_0
  - libssh2=1.11.1=h251f7ec_0
  - libstdcxx=14.1.0=hc0a3c3a_1
  - libstdcxx-ng=14.1.0=h4852527_1
  - libsystemd0=253=h8c4010b_1
  - libtiff=4.4.0=hc85c160_1
  - libtool=2.5.4=h5888daf_0
  - libudev1=253=h0b41bf4_1
  - libunistring=0.9.10=h7f98852_0
  - libuuid=2.38.1=h0b41bf4_0
  - libvorbis=1.3.7=h9c3ff4c_0
  - libwebp-base=1.3.2=h5eee18b_0
  - libxcb=1.15=h0b41bf4_0
  - libxkbcommon=1.7.0=h662e7e4_0
  - libxml2=2.12.7=hc051c1a_1
  - libxslt=1.1.39=h76b75d6_0
  - libzip=1.10.1=h2629f0a_3
  - libzlib=1.2.13=h4ab18f5_6
  - lxml=5.2.2=py310h6a33d3d_0
  - lz4-c=1.9.4=h6a678d5_1
  - matplotlib=3.9.2=py310h06a4308_0
  - matplotlib-base=3.9.2=py310hbfdbfaf_0
  - matplotlib-inline=0.1.7=pyhd8ed1ab_1
  - modeller=10.6=py310h9bf148f_0
  - mpg123=1.32.9=hc50e24c_0
  - multipledispatch=0.6.0=pyhd8ed1ab_1
  - mysql=8.4.0=h721767e_2
  - mysql-common=8.0.33=hf1915f5_6
  - mysql-libs=8.0.33=hca2cd23_6
  - nbconvert-core=7.16.6=pyh29332c3_0
  - nbformat=5.10.4=pyhd8ed1ab_1
  - ncurses=6.4=h6a678d5_0
  - nest-asyncio=1.6.0=pyhd8ed1ab_1
  - notebook-shim=0.2.4=pyhd8ed1ab_1
  - nspr=4.36=h5888daf_0
  - nss=3.98=h1d7d5a4_0
  - numexpr=2.8.7=py310h286c3b5_0
  - numpy=1.26.4=py310heeff2f4_0
  - numpy-base=1.26.4=py310h8a23956_0
  - openjpeg=2.5.0=h7d73246_1
  - openldap=2.6.5=h389dcaa_0
  - openssl=3.4.1=h7b32b05_0
  - outcome=1.3.0.post0=pyhd8ed1ab_1
  - overrides=7.7.0=pyhd8ed1ab_1
  - packaging=24.1=py310h06a4308_0
  - pandas=2.2.2=py310h6a678d5_0
  - parso=0.8.4=pyhd8ed1ab_1
  - pcre2=10.42=hcad00b1_0
  - pexpect=4.9.0=pyhd8ed1ab_1
  - pickleshare=0.7.5=pyhd8ed1ab_1004
  - pillow=11.0.0=py310hfdbf927_0
  - pip=24.2=py310h06a4308_0
  - pixman=0.44.2=h29eaf8c_0
  - pkgutil-resolve-name=1.3.10=pyhd8ed1ab_2
  - ply=3.11=py310h06a4308_0
  - pmw=2.0.1=py310hff52083_1008
  - prometheus_client=0.21.1=pyhd8ed1ab_0
  - prompt_toolkit=3.0.50=hd8ed1ab_0
  - pthread-stubs=0.4=hb9d3cd8_1002
  - ptyprocess=0.7.0=pyhd8ed1ab_1
  - pulseaudio=16.1=hcb278e6_3
  - pulseaudio-client=16.1=h5195f5e_3
  - pulseaudio-daemon=16.1=ha8d29e2_3
  - pure_eval=0.2.3=pyhd8ed1ab_1
  - pybind11-abi=4=hd3eb1b0_1
  - pycairo=1.27.0=py310h25ff670_0
  - pycparser=2.22=pyh29332c3_1
  - pymol-open-source=2.5.0=py310h5b21ba0_6
  - pyparsing=3.1.2=py310h06a4308_0
  - pypng=0.20220715.0=pyhd8ed1ab_1
  - pyqt=6.7.1=py310h6a678d5_0
  - pyqt5-sip=12.13.0=py310h5eee18b_0
  - pyqt6-sip=13.9.1=py310h5eee18b_0
  - pysocks=1.7.1=pyha55dd90_7
  - python=3.10.13=hd12c33a_0_cpython
  - python-dateutil=2.9.0post0=py310h06a4308_2
  - python-fastjsonschema=2.21.1=pyhd8ed1ab_0
  - python-json-logger=2.0.7=pyhd8ed1ab_0
  - python-tzdata=2023.3=pyhd3eb1b0_0
  - python_abi=3.10=2_cp310
  - pytz=2024.1=py310h06a4308_0
  - pyyaml=6.0.2=py310h89163eb_2
  - pyzmq=26.2.0=py310h71f11fc_1
  - qt-main=6.7.2=h06a4308_0
  - qt5compat=6.7.2=h0902c3e_0
  - qtbase=6.7.2=hdaa5aa8_1
  - qtdeclarative=6.7.2=h6a678d5_0
  - qtimageformats=6.7.2=h7fa0f6f_0
  - qtshadertools=6.7.2=h6a678d5_0
  - qtsvg=6.7.2=he621ea3_0
  - qttools=6.7.2=h80c7b02_0
  - qttranslations=6.7.2=h6a678d5_0
  - qtwebchannel=6.7.2=h6a678d5_0
  - qtwebsockets=6.7.2=h6a678d5_0
  - readline=8.2=h5eee18b_0
  - reportlab=4.3.1=py310ha75aee5_0
  - requests=2.32.3=pyhd8ed1ab_1
  - rfc3339-validator=0.1.4=pyhd8ed1ab_1
  - rfc3986-validator=0.1.1=pyh9f0ad1d_0
  - rlpycairo=0.2.0=pyhd8ed1ab_0
  - scipy=1.13.1=py310heeff2f4_0
  - seaborn=0.13.2=py310h06a4308_0
  - selenium=4.30.0=pyh29332c3_0
  - selenium-manager=4.30.0=h6c30b3d_0
  - send2trash=1.8.3=pyh0d859eb_1
  - setuptools=75.1.0=py310h06a4308_0
  - sip=6.10.0=py310h6a678d5_0
  - six=1.16.0=pyhd3eb1b0_1
  - snappy=1.2.1=h6a678d5_0
  - sniffio=1.3.1=pyhd8ed1ab_1
  - sortedcontainers=2.4.0=pyhd8ed1ab_1
  - sqlite=3.45.3=h5eee18b_0
  - stack_data=0.6.3=pyhd8ed1ab_1
  - terminado=0.18.1=pyh0d859eb_0
  - tk=8.6.13=noxft_h4845f30_101
  - tomli=2.0.1=py310h06a4308_0
  - tornado=6.4.1=py310h5eee18b_0
  - toyplot=1.0.3=pyhd8ed1ab_0
  - toytree=2.0.1=pyh9f0ad1d_0
  - tqdm=4.67.1=pyhd8ed1ab_1
  - traitlets=5.14.3=pyhd8ed1ab_1
  - trio=0.29.0=py310hff52083_0
  - trio-websocket=0.12.2=pyh29332c3_0
  - typing_extensions=4.13.0=pyh29332c3_1
  - typing_utils=0.1.0=pyhd8ed1ab_1
  - tzdata=2024b=h04d1e81_0
  - unicodedata2=15.1.0=py310h5eee18b_0
  - uri-template=1.3.0=pyhd8ed1ab_1
  - wcwidth=0.2.13=pyhd8ed1ab_1
  - webencodings=0.5.1=pyhd8ed1ab_3
  - websocket-client=1.8.0=pyhd8ed1ab_1
  - wheel=0.44.0=py310h06a4308_0
  - widgetsnbextension=4.0.13=pyhd8ed1ab_1
  - wsproto=1.2.0=pyhd8ed1ab_1
  - xcb-util=0.4.0=h516909a_0
  - xcb-util-cursor=0.1.4=hd590300_1
  - xcb-util-image=0.4.0=h8ee46fc_1
  - xcb-util-keysyms=0.4.0=h516909a_0
  - xcb-util-renderutil=0.3.9=hd590300_1
  - xcb-util-wm=0.4.1=h516909a_0
  - xkeyboard-config=2.38=h0b41bf4_0
  - xorg-kbproto=1.0.7=hb9d3cd8_1003
  - xorg-libice=1.1.2=hb9d3cd8_0
  - xorg-libsm=1.2.6=he73a12e_0
  - xorg-libx11=1.8.9=h8ee46fc_0
  - xorg-libxau=1.0.12=hb9d3cd8_0
  - xorg-libxdmcp=1.1.5=hb9d3cd8_0
  - xorg-libxext=1.3.4=h0b41bf4_2
  - xorg-libxrender=0.9.11=hd590300_0
  - xorg-renderproto=0.11.1=hb9d3cd8_1003
  - xorg-xextproto=7.3.0=hb9d3cd8_1004
  - xorg-xproto=7.0.31=hb9d3cd8_1008
  - xz=5.4.6=h5eee18b_1
  - yaml=0.2.5=h7f98852_2
  - zeromq=4.3.5=h59595ed_1
  - zipp=3.21.0=pyhd8ed1ab_1
  - zlib=1.2.13=h4ab18f5_6
  - zstandard=0.23.0=py310ha75aee5_1
  - zstd=1.5.6=ha6fb4c9_0
  - pip:
      - anyio==4.6.0
      - asttokens==2.4.1
      - async-lru==2.0.4
      - babel==2.16.0
      - beautifulsoup4==4.12.3
      - biopython==1.85
      - bleach==6.1.0
      - bottle==0.13.2
      - brotli==1.1.0
      - certifi==2024.8.30
      - charset-normalizer==3.4.0
      - debugpy==1.8.7
      - decorator==5.1.1
      - ete4==4.0.0b2
      - fastjsonschema==2.20.0
      - httpcore==1.0.6
      - httpx==0.27.2
      - ipython==8.28.0
      - jedi==0.19.1
      - jinja2==3.1.4
      - json5==0.9.25
      - jupyter-events==0.10.0
      - jupyter-server==2.14.2
      - markupsafe==3.0.1
      - mistune==3.0.2
      - nbclient==0.10.0
      - nbconvert==7.16.4
      - notebook==7.2.2
      - pandocfilters==1.5.1
      - platformdirs==4.3.6
      - prometheus-client==0.21.0
      - prompt-toolkit==3.0.48
      - psutil==6.0.0
      - pygments==2.18.0
      - python-dotenv==1.1.0
      - ramachandraw==1.0.1
      - referencing==0.35.1
      - rpds-py==0.20.0
      - soupsieve==2.6
      - tinycss2==1.3.0
      - types-python-dateutil==2.9.0.20241003
      - typing-extensions==4.12.2
      - urllib3==2.2.3
      - webcolors==24.8.0
      - webdriver-manager==4.0.2
      - wget==3.2
```
</details>

### TM-align

Forked from https://zhanggroup.org/TM-align/ [^1].

[^1]: Zhang, Y. TM-align: a protein structure alignment algorithm based on the TM-score. Nucleic Acids Research 33, 2302–2309. issn: 1362-4962. http://dx.doi.org/10.1093/nar/gki524 (Apr. 2005).

```
cd tmalign
g++ -static -O3 -ffast-math -lm -o TMalign TMalign.cpp
chmod +x ./TMalign
```

### GROMACS

https://manual.gromacs.org/current/download.html [^2]

```
cd gromacs
tar xfz gromacs-2024.2.tar.gz
cd gromacs-2024.2
mkdir build
cd build
cmake .. -DGMX_BUILD_OWN_FFTW=ON -DREGRESSIONTEST_DOWNLOAD=ON
make
make check
sudo make install
source /usr/local/gromacs/bin/GMXRC
```

For cuda users,
```
cmake .. -DGMX_BUILD_OWN_FFTW=ON -DREGRESSIONTEST_DOWNLOAD=ON -DGMX_GPU=CUDA -DCMAKE_CUDA_COMPILER=/usr/local/cuda/bin/nvcc
```

`min_sd.mdp`, `nvt_heat.mdp`, `npt_prod.mdp`, `npt_eq.mdp`, `to_origin.tcl`, `del_wat_inside.tcl` are derived from
https://github.com/allison-group/structural-phylogenetics-bootstrap/blob/master/MD/GMX/.

[^2]: Abraham, M. J. et al. GROMACS: High performance molecular simulations through multi-level parallelism from laptops to supercomputers. SoftwareX 1–2, 19–25. issn: 2352-7110. http://dx.doi.org/10.1016/j.softx.2015.06.001 (Sept. 2015).

### CHARMM36 Force Field for GROMACS

https://mackerell.umaryland.edu/charmm_ff.shtml#gromacs

charmm36-jul2022.ff.tgz (July 2022, ver.)
https://mackerell.umaryland.edu/download.php?filename=CHARMM_ff_params_files/charmm36-jul2022.ff.tgz

```
cd gromacs
tar xfz charmm36-jul2022.ff.tgz
```

### VMD

Download VMD (e.g., `vmd-1.9.4a57.bin.LINUXAMD64-CUDA102-OptiX650-OSPRay185.opengl.tar.gz`) from 
https://www.ks.uiuc.edu/Research/vmd/ to `./vmd`.

```
cd vmd
tar xfz vmd-1.9.4a57.bin.LINUXAMD64-CUDA102-OptiX650-OSPRay185.opengl.tar.gz
cd vmd-1.9.4a57
./configure
cd src
sudo make install
```

### Autodock Vina

https://vina.scripps.edu/

```
conda install conda-forge::vina
```

### ADFR Suite

https://ccsb.scripps.edu/adfr/downloads/

```
conda install hcc::adfr-suite
```

### Reduce

```
conda install bioconda::reduce
```

### ClustalW / ClustalO

```
conda install bioconda::clustalw
conda install bioconda::clustalo
```

### Modeller

```
conda install salilab::modeller
```

### Emboss

```
conda install bioconda::emboss
```

### MGL TOOLS

```
conda install bioconda::mgltools
```