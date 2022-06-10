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


#### La base de datos se tomÃ³ del CENSO 2020, secciÃ³n Datos Abiertos.

#### Se descargan Ãºnicamente los datos del estado de Veracruz del siguiente link general:

* https://www.inegi.org.mx/programas/ccpv/2020/#Datos_abiertos

#### Link directo a la url de los Principales Resultados por Localidad (ITER)

* https://www.inegi.org.mx/contenidos/programas/ccpv/2020/datosabiertos/iter/iter_30_cpv2020_csv.zip

#### Limpiamos nuestro entorno
rm(list = ls())

#### URL de datos de Veracruz
url <- "https://www.inegi.org.mx/contenidos/programas/ccpv/2020/datosabiertos/iter/iter_30_cpv2020_csv.zip"

#### Establecer directorio de trabajo y crear carpeta de extracciÃ³n. Es importante aclarar que el Knit no se puede usar el setwd(), por lo tanto, hay que codificar el el cambio de directorio de trabajo desde el setup de knit.  

raiz=setwd("/Users/ed...")
dir.create("Datos",showWarnings = F)
directorio=paste0(raiz,"/Datos")
setwd(directorio)

