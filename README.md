# Hub de Hardening y Resiliencia DoS HTTP/2 y Kernel Linux

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-5b3cf5.svg)](https://tavardt-espana.github.io/http2-kernel-dos-resilience-checker-es/)
[![Jurisdicción](https://img.shields.io/badge/Jurisdicci%C3%B3n-Espa%C3%B1a-00C853.svg)](https://ag.tavardt.com/es/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![RFC 7540](https://img.shields.io/badge/RFC-7540-blue.svg)](https://datatracker.ietf.org/doc/html/rfc7540)
[![RFC 9113](https://img.shields.io/badge/RFC-9113-blue.svg)](https://datatracker.ietf.org/doc/html/rfc9113)

**Hub de Arquitectura Defensiva y Mitigación contra DoS en HTTP/2 (Rapid Reset CVE-2023-44487) y Kernel Linux**

Desarrollado y mantenido por la división de ingeniería de seguridad e infraestructura de **[TAVARDT Espana](https://ag.tavardt.com/es/)**.

***

## Portales Oficiales

* **Portal Institucional**: [https://ag.tavardt.com/es/](https://ag.tavardt.com/es/)
* **Central de Herramientas**: [https://tools.tavardt.com/es/](https://tools.tavardt.com/es/)
* **Canal de Atención y Soporte Técnico**: [https://ag.tavardt.com/es/contacto/](https://ag.tavardt.com/es/contacto/)

***

## Demostración Online y Hub de Arquitectura Defensiva

Puede consultar la especificación tecnica corporativa, las pruebas de diagnóstico arquitectónico y los blueprints de mitigación directamente desde el navegador:

* **[Aplicación Web Oficial en GitHub Pages](https://tavardt-espana.github.io/http2-kernel-dos-resilience-checker-es/)**
* **[Central de Herramientas TAVARDT](https://tools.tavardt.com/es/)**

> [!NOTE]
> **Alcance de Ejecución Técnica:** Este hub web proporciona especificaciónes de arquitectura defensiva y blueprints de configuración. Las auditorías activas de caída de kernel y resiliencia TCP requieren privilegios de sistema (root) y ejecución directa en el servidor host mediante la herramienta CLI oficial (`http2_kernel_dos_checker.py`). Las páginas web en entornos sandbox de navegador no pueden auditar parámetros internos del kernel.

***

## Blueprints Técnicos de Hardening

1. **sysctl-hardening.conf:** Parámetros optimizados en `/proc/sys/net/ipv4` mitigando inundaciones SYN, ataques de timestamp NoisyTCP y agotamiento de sockets huérfanos.
2. **nginx-http2-hardened.conf:** Configuración de proxy inverso NGINX blindada imponiendo límites estrictos de concurrencia (`http2_max_concurrent_streams 64`) y rate limiting riguroso de tramas RST_STREAM.
3. **nftables-dos-protection.conf:** Reglas de filtrado de paquetes de Capa 4 descartando ráfagas anómalas TCP SYN y RST antes de la asignación de sockets en el kernel.
4. **docker-compose-hardened.yml:** Arquitectura de contenedores aislados aplicando límites de recursos (memoria, CPU, ulimits) a proxies web perimetrales.
5. **http2_kernel_dos_checker.py:** Utilidad CLI local determinista ejecutada con privilegios de sistema en el servidor para auditar directamente parámetros `/proc/sys` y verificar cumplimiento de RFCs.

***

## Uso de la Herramienta CLI Determinista

Para ejecutar la inspección determinista directamente en el host del servidor Linux:

```bash
# 1. Descargar script de auditoría desde el repositorio oficial
curl -sO https://raw.githubusercontent.com/TAVARDT-Espana/http2-kernel-dos-resilience-checker-es/main/http2_kernel_dos_checker.py

# 2. Inspeccionar parámetros locales del kernel Linux
sudo python3 http2_kernel_dos_checker.py -kernel

# 3. Exportar diagnóstico en formato estructurado JSON
sudo python3 http2_kernel_dos_checker.py -kernel -json
```

***

## Gobernanza y Soberania

* **Organización:** TAVARDT-Espana
* **Jurisdicción:** Espana
* **Cumplimiento de Estándares:** CIS Linux Benchmarks, RFC 7540, RFC 9113, CVE-2023-44487 y Arquitectura Zero Trust.

Desarrollado por la División de Ciberseguridad e Infraestructura de **[TAVARDT Espana](https://ag.tavardt.com/es/)**. Todos los derechos reservados.
