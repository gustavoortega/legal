---
title: PiHelm — Privacy Policy
---

# PiHelm — Privacy Policy

**Effective date:** 2026-05-04
**Last updated:** 2026-05-04
**Version:** 1.0.0

PiHelm ("the app") is an iOS application that lets you monitor and manage Raspberry Pi devices over SSH. This policy explains what data the app handles and how.

[Cambiar a Español](#política-de-privacidad-español)

## TL;DR

PiHelm does not collect, transmit, or store any personal data on external servers. Everything stays on your device.

## What data the app handles

### Stored locally on your device

- **Raspberry Pi connection profiles** (name, IP/hostname, username, port, auth method) — stored in iOS UserDefaults.
- **SSH credentials** (passwords or RSA private keys) — stored encrypted in the iOS Keychain. Never written to disk in plain text.
- **Sudo passwords** (when you enable them) — stored encrypted in the iOS Keychain, separately from SSH credentials.
- **Custom commands you create** — stored in iOS UserDefaults.
- **Metric history samples** (CPU, RAM, temperature, disk, network, per-core CPU, throttling) — stored in a local SwiftData database, automatically pruned after 24 hours.
- **App settings** (alert thresholds, card visibility, language) — stored in iOS UserDefaults.
- **Trial status** — stored in iOS Keychain and iCloud Key-Value Store (under your Apple ID, syncs across your devices).

### Transmitted

- **SSH commands and their output** — sent encrypted (SSH protocol) directly to your Raspberry Pi. The connection is peer-to-peer; PiHelm does not route traffic through any intermediate server.

### Sent to third parties

- **None.** PiHelm does not include any analytics, advertising, crash reporting, or telemetry SDKs.

## In-App Purchases

PiHelm offers a one-time in-app purchase ("PiHelm Pro") to unlock advanced features. Payment is processed entirely by Apple via the App Store. Apple shares with us only the anonymous receipt confirming the purchase status; we do not receive your name, email, or payment information.

A 7-day free trial of Pro features starts automatically on first launch. The trial start date is stored in your iOS Keychain and (if iCloud is enabled) synced via iCloud Key-Value Store under your Apple ID, which prevents the trial from being reset by reinstalling the app.

## Notifications

If you enable alerts, PiHelm uses Apple's local notification system (`UNUserNotificationCenter`) to display notifications based on metrics fetched from your Raspberry Pi. Notifications are generated entirely on-device. Nothing is sent to any external service.

When in background, PiHelm uses iOS's `BGAppRefreshTask` to periodically (every 15-60 minutes, controlled by iOS) connect to your last-used Pi, fetch metrics, evaluate alert thresholds, and fire local notifications if needed. This requires "Background App Refresh" enabled in iOS Settings.

## Network usage

PiHelm uses the iOS Local Network entitlement to discover and connect to Raspberry Pi devices on your local network or any IP/hostname you configure. The app requests permission the first time you attempt to connect. iOS will show a system prompt asking for your consent.

## Children's privacy

PiHelm is not directed at children under 13 and does not knowingly collect any data from anyone, including children.

## Data deletion

To remove all PiHelm data from your device:

1. Open Settings → General → iPhone Storage → PiHelm → Delete App.

This wipes all profiles, Keychain entries, history, and settings stored locally on the device.

To remove individual Pi profiles inside the app: long-press a Pi in the list → Delete. The associated Keychain credentials are removed as well.

To clear the iCloud-synced trial date (after uninstalling, if you want to start over): Settings → [your Apple ID] → iCloud → Manage Storage → PiHelm → Delete data.

## Open source dependencies

PiHelm uses [Citadel](https://github.com/orlandos-nl/Citadel) (an open-source Swift SSH library) and Apple's [swift-nio](https://github.com/apple/swift-nio) and [swift-crypto](https://github.com/apple/swift-crypto) for the SSH protocol implementation. These libraries run entirely on-device and do not transmit data anywhere except to your configured SSH endpoint.

## Changes to this policy

If we materially change this policy, we will update the "Last updated" date and post the new version at the URL where you found this document. The full history of changes is publicly available in [CHANGELOG.md](./CHANGELOG.md) and via the [git history](https://github.com/gustavoortega/legal/commits/main/pihelm/index.md) of this document.

## Contact

For privacy questions about PiHelm: [gortega+pihelm@gmail.com](mailto:gortega+pihelm@gmail.com)

For security issues affecting this policy or the app: see [SECURITY.md](../SECURITY.md)

---

# Política de Privacidad (Español)

**Fecha de vigencia:** 2026-05-04
**Última actualización:** 2026-05-04
**Versión:** 1.0.0

PiHelm ("la app") es una aplicación iOS que te permite monitorear y gestionar dispositivos Raspberry Pi por SSH. Esta política explica qué datos maneja la app y cómo.

## Resumen

PiHelm no recopila, transmite ni almacena datos personales en servidores externos. Todo permanece en tu dispositivo.

## Qué datos maneja la app

### Guardados localmente en tu dispositivo

- **Perfiles de Raspberry Pi** (nombre, IP/hostname, usuario, puerto, método de auth) — UserDefaults de iOS.
- **Credenciales SSH** (contraseñas o llaves privadas RSA) — Keychain de iOS, cifradas. Nunca se escriben en disco en texto plano.
- **Contraseñas sudo** (cuando las habilitás) — Keychain de iOS, cifradas, separadas de las credenciales SSH.
- **Comandos personalizados** — UserDefaults de iOS.
- **Histórico de métricas** (CPU, RAM, temperatura, disco, red, CPU por core, throttling) — base SwiftData local, se purga automáticamente a las 24h.
- **Configuraciones de la app** (umbrales de alerta, visibilidad de cards, idioma) — UserDefaults de iOS.
- **Estado del trial** — Keychain de iOS + iCloud Key-Value Store (bajo tu Apple ID, sincroniza entre tus dispositivos).

### Transmitido

- **Comandos SSH y su respuesta** — enviados cifrados (protocolo SSH) directamente a tu Raspberry Pi. La conexión es punto a punto; PiHelm no enruta tráfico por ningún servidor intermedio.

### Enviado a terceros

- **Nada.** PiHelm no incluye SDKs de analytics, publicidad, crash reporting ni telemetría.

## Compras in-app

PiHelm ofrece una compra única ("PiHelm Pro") para desbloquear funciones avanzadas. El pago lo procesa completamente Apple via App Store. Apple solo nos comparte el recibo anónimo confirmando el estado de la compra; no recibimos tu nombre, email ni datos de pago.

Un trial gratuito de 7 días de Pro arranca automáticamente al primer launch. La fecha de inicio del trial se guarda en el Keychain de iOS y (si tenés iCloud habilitado) se sincroniza via iCloud Key-Value Store bajo tu Apple ID, lo que evita que se pueda resetear el trial reinstalando la app.

## Notificaciones

Si habilitás alertas, PiHelm usa el sistema de notificaciones locales de Apple (`UNUserNotificationCenter`) para mostrar notificaciones basadas en métricas obtenidas de tu Raspberry Pi. Las notificaciones se generan enteramente on-device. No se envía nada a ningún servicio externo.

En background, PiHelm usa `BGAppRefreshTask` de iOS para conectarse periódicamente (cada 15-60 minutos, lo controla iOS) a tu última Pi usada, obtener métricas, evaluar umbrales de alerta y disparar notificaciones locales si corresponde. Requiere "Background App Refresh" habilitado en Ajustes de iOS.

## Uso de red

PiHelm usa el entitlement de Local Network de iOS para descubrir y conectarse a dispositivos Raspberry Pi en tu red local o cualquier IP/hostname que configures. La app pide permiso la primera vez que intentás conectar. iOS muestra un prompt del sistema pidiendo tu consentimiento.

## Privacidad de menores

PiHelm no está dirigida a menores de 13 años y no recopila conscientemente datos de ninguna persona, incluyendo menores.

## Borrado de datos

Para borrar todos los datos de PiHelm de tu dispositivo:

1. Abrí Ajustes → General → Almacenamiento del iPhone → PiHelm → Eliminar app.

Esto borra todos los perfiles, entradas del Keychain, histórico y configuraciones guardadas localmente.

Para borrar perfiles de Pi individuales desde dentro de la app: long-press en una Pi de la lista → Eliminar. Las credenciales asociadas en el Keychain también se borran.

Para limpiar la fecha del trial sincronizada en iCloud (después de desinstalar, si querés empezar de cero): Ajustes → [tu Apple ID] → iCloud → Administrar almacenamiento → PiHelm → Borrar datos.

## Dependencias open source

PiHelm usa [Citadel](https://github.com/orlandos-nl/Citadel) (librería SSH open source en Swift) y [swift-nio](https://github.com/apple/swift-nio) y [swift-crypto](https://github.com/apple/swift-crypto) de Apple para implementar el protocolo SSH. Estas librerías corren enteramente on-device y no transmiten datos a ningún lado salvo al endpoint SSH que vos configures.

## Cambios a esta política

Si cambiamos materialmente esta política, actualizaremos la fecha "Última actualización" y publicaremos la versión nueva en la URL donde encontraste este documento. El historial completo de cambios está públicamente disponible en [CHANGELOG.md](./CHANGELOG.md) y via el [historial git](https://github.com/gustavoortega/legal/commits/main/pihelm/index.md) de este documento.

## Contacto

Para preguntas de privacidad sobre PiHelm: [gortega+pihelm@gmail.com](mailto:gortega+pihelm@gmail.com)

Para issues de seguridad que afecten esta política o la app: ver [SECURITY.md](../SECURITY.md)
