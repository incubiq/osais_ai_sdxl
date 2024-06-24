##
##      To build the AI_SDXL docker image
##

# base stuff
FROM yeepeekoo/public:ai_sdxl_


###### update latest OSAIS config (not an absolute requirement) ######

# push again the base files
COPY ./_static/* ./_static
COPY ./_templates/* ./_templates
COPY ./_osais/* .

# copy warmup files
COPY ./_input/warmup.jpg ./_input/warmup.jpg


###### specific AI config (must do) ######
COPY ./ai/model ./ai/model
COPY ./ai/models ./ai/models
COPY ./ai/configs ./ai/configs
COPY ./ai/ldm ./ai/ldm
COPY ./ai/src ./ai/src
COPY ./ai/scripts ./ai/scripts
COPY ./ai/runai.py ./ai/runai.py

# overload config with those default settings
ENV ENGINE=sdxl

# run as a server
CMD ["uvicorn", "main_fastapi:app", "--host", "0.0.0.0", "--port", "5111"]
