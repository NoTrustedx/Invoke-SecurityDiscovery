# Invoke-SecurityDiscovery.ps1
PowerShell script para el **descubrimiento de software de seguridad en sistemas Windows**. Este script permite realizar una auditoría local o remota sobre herramientas de defensa activas, servicios, procesos relacionados con seguridad y configuraciones de Windows Defender.

## 🧰 Funcionalidad

`Invoke-SecurityDiscovery.ps1` realiza las siguientes acciones:

- ✅ Obtiene el estado del firewall de Windows y sus reglas activas
- ✅ Enumera servicios y procesos relacionados con herramientas de seguridad (antivirus, EDR, Sysmon, etc.)
- ✅ Detecta la presencia y ejecución de Sysmon
- ✅ Consulta información de antivirus mediante WMI (`Get-CimInstance` y `Get-WmiObject`)
- ✅ Muestra las exclusiones activas de Windows Defender

## 💻 Uso

### Ejecución local

```powershell
.\Invoke-SecurityDiscovery.ps1
````

### Ejecución remota con salida detallada

```powershell
.\Invoke-SecurityDiscovery.ps1 -ComputerName "EQUIPO-REMOTO" -EnableVerbose
```

## 📥 Parámetros

| Parámetro        | Descripción                                                              |
| ---------------- | ------------------------------------------------------------------------ |
| `-ComputerName`  | Nombre del equipo donde se ejecutará el script (por defecto: local)      |
| `-EnableVerbose` | Muestra información adicional durante la ejecución del script (opcional) |

## 📌 Ejemplo de salida

```powershell
[+] Información del Firewall:
Name     Enabled
----     -------
Domain   True
Private  True
Public   True

[+] Servicios y procesos relacionados con seguridad:
Name       DisplayName         Status
----       -----------         ------
WinDefend  Windows Defender AV Running
Sysmon     Sysmon64            Running

[+] Detección de Sysmon:
Sysmon está en ejecución.
385201  SysmonDrv

[+] Software de seguridad mediante WMI:
displayName     pathToSignedProductExe                 productState
------------    ------------------------               -------------
Windows Defender C:\Program Files\Windows Defender...  397568

[+] Exclusiones de Windows Defender:
ExclusionPath      ExclusionExtension  ExclusionProcess  DisableRealtimeMonitoring
--------------      ------------------  -----------------  -------------------------
C:\Tools\Hacking    .ps1                nmap.exe          False
```
## 🔒 Requisitos

* Ejecutar como **Administrador**
* Compatible con **Windows 10/11**, Windows Server 2016+
* PowerShell 5.1+

## 📂 Archivos

* `Invoke-SecurityDiscovery.ps1` – Script principal
* `README.md` – Documentación
* `LICENSE` – Licencia MIT (opcional)

## ⚠️ Consideraciones

* Este script está pensado con fines de **auditoría defensiva y educativa**.
* El uso en entornos Red Team debe estar autorizado bajo contrato o acuerdo de pruebas de penetración.

## 👨‍💻 Autor

ErickO. – [@tuusuario](https://github.com/NoTrustedx)

## 📄 Licencia

MIT License – libre para uso, modificación y distribución bajo los términos de la licencia.
