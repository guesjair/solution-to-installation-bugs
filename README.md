```markdown
# Solución al Problema de Ejecución de Scripts en PowerShell para la Creación de Proyecto React con Vite

Al intentar ejecutar el comando:

```powershell
PS C:\tallereact> npm create vite@latest
```

Puedes encontrarte con el siguiente error:

```plaintext
npm : No se puede cargar el archivo C:\Program Files\nodejs\npm.ps1 porque la ejecución de scripts está deshabilitada
en este sistema. Para obtener más información, consulta el tema about_Execution_Policies en: 
https:/go.microsoft.com/fwlink/?LinkID=135170.
En línea: 1 Carácter: 1
+ npm create vite@latest
+ 
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

Este error se debe a que **PowerShell tiene una política de ejecución de scripts deshabilitada de manera predeterminada para proteger el sistema**. Para solucionar este problema, tienes que cambiar la política de ejecución de PowerShell.

## Sigue estos pasos:

1. **Abre PowerShell con permisos de administrador**. Puedes hacer esto buscando "PowerShell" en el menú de inicio, haciendo clic derecho sobre "Windows PowerShell" y seleccionando "Ejecutar como administrador".

2. **Cambia la política de ejecución a "RemoteSigned" o "Unrestricted"**. La política "RemoteSigned" permite ejecutar scripts locales sin firmar y requiere que los scripts descargados de Internet estén firmados por un editor de confianza. La política "Unrestricted" permite ejecutar cualquier script sin restricciones. Usa el siguiente comando para cambiar la política de ejecución:

   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

   O

   ```powershell
   Set-ExecutionPolicy Unrestricted
   ```

3. **Cuando se te pregunte si deseas cambiar la política de ejecución, escribe "Y" y presiona Enter**.

4. **Vuelve a ejecutar el comando `npm create vite@latest`**.

## Ejemplo paso a paso:

```powershell
# Abrir PowerShell como administrador y ejecutar el siguiente comando
Set-ExecutionPolicy RemoteSigned
# Confirmar el cambio de política
Y

# Luego, navega a tu directorio del proyecto y ejecuta el comando npm
cd .\tallereact\
npm create vite@latest
```

Después de cambiar la política de ejecución, deberías poder ejecutar el comando `npm create vite@latest` sin problemas. Si prefieres restablecer la política de ejecución a su valor predeterminado después de ejecutar tu comando npm, puedes usar:

```powershell
Set-ExecutionPolicy Restricted
```
