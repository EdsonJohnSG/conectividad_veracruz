# conectividad_veracruz

#### Este archivo contiene cÃ³digo para generar indicadores de conectividad de los diferentes municipios de veracruz. Por ejemplo:
* Porcentaje total de hogares con internet.
* Porcentaje total de hogares con acceso a un celular.
* Porcentaje total de hogares con acceso a television.
* Porcentaje total de hogares con acceso a PC.
* Porcentaje total de hogares sin acceso a internet. 
* Porcentaje total de hogares sin acceso a una PC.
* Porcentaje total de hogares sin acceso a las tecnlogias de la comunicacion. 


#### La base de datos se tomó del CENSO 2020, sección Datos Abiertos.

#### Se descargan únicamente los datos del estado de Veracruz del siguiente link:

* https://www.inegi.org.mx/programas/ccpv/2020/#Datos_abiertos

### Limpiamos nuestro entorno
rm(list = ls())

### Importamos las librerias que utilizaremos, en este caso tidyverse y dplyr.
library(readxl)
library(tidyverse)
library(ggplot2)
library(dplyr)

### Se importa la base de datos del estado de Veracruz
Veracruz <- read.csv("conjunto_de_datos_iter_30CSV20.csv")
View(Veracruz)

### Paso 1: Se eligen solo las variables que se utilizarán para construir los indicadores de conectividad antes descritos.
### Paso 2: Con la función filter () se filtran sólo las filas que contienen la información agregada de cada municipio de Veracruz.
### Paso 3: Con la función mutate() se crean nuevas columnas que correspoden a los indicadores de conectividad que nos interesa construir. 
### Paso 4: Con la función mutate () se crea la variable "categoría_internet"" para determinar si por el indicador de porcentaje total de hogares con internet de cada municipio, pertenece a una categoría de acceso de internet "Muy Bajo", "Bajo", "Medio" o "Alto"

Base_2<- select(Veracruz,"ENTIDAD", "NOM_ENT", "MUN", "NOM_MUN","LOC","NOM_LOC","VPH_RADIO",
                "VPH_TV",  "VPH_PC", "VPH_TELEF", "VPH_CEL",
                "VPH_INTER", "TOTHOG", "VPH_SINTIC","VPH_SINCINT","VIVTOT") %>%  
  filter(NOM_LOC=="Total del Municipio") %>% 
  mutate(Porcentaje_Internet=as.numeric(VPH_INTER)/as.numeric(VIVTOT)*100) %>% 
  mutate(Porcentaje_Celular=as.numeric(VPH_CEL)/as.numeric(VIVTOT)*100) %>% 
  mutate(Porcentaje_TV=as.numeric(VPH_TV)/as.numeric(VIVTOT)*100) %>% 
  mutate(Porcentaje_PC=as.numeric(VPH_PC)/as.numeric(VIVTOT)*100) %>% 
  mutate(Porcentaje_SinInternet_PC=as.numeric(VPH_SINCINT)/as.numeric(VIVTOT)*100) %>% 
  mutate(Porcentaje_SinTic=as.numeric(VPH_SINTIC)/as.numeric(VIVTOT)*100) %>% 
  mutate(Categoria_internet=cut(Porcentaje_Internet,breaks = c(0,11.85,18.98,27.46,Inf), 
  labels = c("Muy bajo", "bajo", "medio", "alto")))





