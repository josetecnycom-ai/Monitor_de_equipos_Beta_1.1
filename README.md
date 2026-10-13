# Monitor de Frigoríficos — Beta v1.1

Add-in para **MyGeotab** que permite monitorizar en tiempo real el estado y salud de la cadena de frío en remolques y vehículos frigoríficos: comunicación del dispositivo principal (GO, Teltonika, etc.), detección de módulos IOX (uReader / IOX-COLD), estado y modelo del termógrafo/sondas, temperaturas por zonas y máquina de frío.

## Características

- **Monitor de salud de la flota**: Supervisión global en tiempo real categorizada por grupo de vehículos/remolques.
- **Buscador en tiempo real**: Filtrado instantáneo por nombre de activo.
- **Filtros rápidos**:
  - *Mostrar solo activos con problema* (excluye los que están en estado OK).
  - *Ocultar sin máquina de frío* (para centrarse en semirremolques con máquina activa).
- **Indicadores de estado numéricos (Zenith Cards)**:
  - OK
  - Dispositivo sin comunicar (> 48h)
  - IOX no detectado / desconectado (> 48h)
  - Termógrafo/Sondas con problema (códigos de error de termógrafo o > 48h sin lecturas)
  - Máquina de frío sin datos (> 48h)
- **Tabla con encabezado fijo (Sticky Header)**: Navegación cómoda con scroll vertical manteniendo los títulos visibles.
- **Exportación a Excel / CSV**: Descarga inmediata con soporte completo para caracteres especiales y grados (°C) bajo estándar UTF-8 con BOM.
- **Exclusión automática de activos archivados**: Evita falsos positivos en vehículos dados de baja.
- **Diseño Geotab Zenith**: Interfaz integrada con el sistema de diseño oficial de Geotab (tipografía Nunito Sans, paleta corporativa `#0064A8`, tarjetas y chips).
- **Insignia "Beta"**: Identificador visual según las guías Zenith Storybook de Geotab.

## Instalación en MyGeotab

1. Sube este repositorio a GitHub bajo el nombre **Monitor_de_equipos_Beta_1.1**.
2. En GitHub > Settings > Pages, activa **GitHub Pages** para la rama `main` o `master`.
3. Asegúrate de que la URL en `config.json` coincida con:  
   `https://<tu-usuario>.github.io/Monitor_de_equipos_Beta_1.1/index.html`
4. En **MyGeotab**:
   - Ve a **Administración** > **Sistema** > **Add-Ins**.
   - Haz clic en **Añadir Add-In** y sube el archivo `config.json` (o pega su contenido JSON).
   - Guarda los cambios.

## Diagnósticos evaluados

| Componente | Identificador de Diagnóstico | Descripción |
|------------|------------------------------|-------------|
| Dispositivo principal | `DeviceStatusInfo` | Comunicación activa y fecha de último contacto |
| uReader | `DiagnosticExternalDeviceIntendiaId`, `azRjqdVaIxkSmbO5V-0khgA` | Hardware uReader / Intendia detectado |
| IOX-COLD | `DiagnosticExternalDeviceIOXColdChainId` | Módulo IOX Cold Chain |
| IOX Conexión | `DiagnosticIOXColdConnectionStatusId`, `DiagnosticIOXColdRuggedConnectionStatusId` | Estado de conexión física del bus IOX |
| Termógrafo Z1/Z2 | `ThermographTemperature1Id`, `ThermographTemperature2Id` | Temperaturas de las zonas de carga |
| Estado Termógrafo | `ThermographStatusId` | Estado operativo (0: Deshabilitado, 1: Activo, 2: Desactivado, 3: Error) |
| Modelo Termógrafo | `a5IuZRNSymkS_lkDlsgRgpg` | Modelo identificado (Euroscan, Transcan, Datacold, etc.) |
| Sondas remotas | `RemoteProbe1TemperatureId`, `RemoteProbe2TemperatureId`, `RemoteProbe3TemperatureId` | Sensores cableados/inalámbricos |
| Máquina de frío | `RefrigerationUnitStatusId`, temperaturas de consigna y retorno | Unidad frigorífica |

## Tecnologías

- Geotab Zenith Design System (CSS vanilla encapsulado)
- Tipografía Nunito Sans (Google Fonts)
- Geotab API SDK (multiCall optimizado por lotes)
