# Domus

Proyecto full-stack separado en frontend y backend, organizado con la misma estructura base usada en `Hospital Familia`.

Estado del alcance funcional recuperado: `100%`.
Las mejoras de infraestructura productiva que no pertenecen a esos módulos se
mantienen separadas en el roadmap.

## Estructura

```text
Domus/
  base/          # Documentos fuente o insumos base del proyecto
  docs/          # Documentacion funcional, tecnica y ruta de trabajo
  domus-app/     # Frontend
  domus-server/  # Backend
  prompts/       # Prompts reutilizables para trabajo con agentes
```

## Repositorios

- Frontend: `https://github.com/Cristianlr95/domus-app`
- Backend: `https://github.com/Cristianlr95/domus-server`

## Uso

Este repositorio padre funciona como punto de entrada documental del proyecto. El codigo de aplicacion se mantiene en los repositorios `domus-app` y `domus-server`.

El trabajo se integra primero en `develop` y luego se incorpora a `main` en ambos repositorios.

Las brechas productivas conocidas se mantienen en [docs/ROADMAP.md](docs/ROADMAP.md).
