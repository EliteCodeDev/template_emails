# Variables de configuración para los templates de correo electrónico

## Configuraciones para Neo Capital

```json
{
  "COMPANY_NAME": "Neocapital",
  "LOGO_URL": "https://example.com/neo-logo.png",
  "COMPANY_ADDRESS": "123 Trading St., Financial District, New York, NY 10005",
  "SUPPORT_URL": "https://neocapital.com/support",
  "UNSUBSCRIBE_URL": "https://neocapital.com/unsubscribe",
  "PRIVACY_URL": "https://neocapital.com/privacy",
  "IMAGE_URL": "https://neocapital.com/images",

  "EMAIL_BG_COLOR": "#fffbeb",
  "CONTAINER_BG_COLOR": "#111111",
  "HEADER_BG_COLOR": "#000000",
  "HERO_BG_COLOR": "#1a1a1a",
  "FOOTER_BG_COLOR": "#000000",
  "CARD_BG_COLOR": "rgba(17, 17, 17, 0.9)",
  "TICKET_BG_COLOR": "rgba(17, 17, 17, 0.8)",

  "ACCENT_COLOR": "#f59e0b",
  "SECONDARY_TEXT_COLOR": "#fef3c7",
  "LABEL_COLOR": "#f59e0b",
  "FOOTER_TEXT_COLOR": "#d1d5db",
  "STATUS_COLOR": "#f59e0b",
  "STATUS_BG_COLOR": "rgba(245, 158, 11, 0.1)",

  "SHADOW_COLOR": "rgba(245, 158, 11, 0.2)",
  "BORDER_COLOR": "rgba(245, 158, 11, 0.2)",
  "CARD_BORDER_COLOR": "rgba(245, 158, 11, 0.3)",
  "DIVIDER_COLOR": "rgba(245, 158, 11, 0.2)",

  "HIGHLIGHT_COLOR": "rgba(245, 158, 11, 0.2)",
  "HIGHLIGHT_BG_COLOR": "rgba(245, 158, 11, 0.05)",
  "WARNING_COLOR": "#f59e0b",
  "WARNING_BG_COLOR": "rgba(245, 158, 11, 0.1)",

  "SOCIAL_LINKS": {
    "facebook": "https://facebook.com/neocapital",
    "twitter": "https://twitter.com/neocapital",
    "instagram": "https://instagram.com/neocapital"
  }
}
```

## Configuraciones para Zeven Global

```json
{
  "COMPANY_NAME": "ZevenGlobal",
  "LOGO_URL": "https://example.com/zeven-logo.png",
  "COMPANY_ADDRESS": "456 Forex Ave., Trading Hub, London, UK WC2N 5DU",
  "SUPPORT_URL": "https://zevenglobal.com/support",
  "UNSUBSCRIBE_URL": "https://zevenglobal.com/unsubscribe",
  "PRIVACY_URL": "https://zevenglobal.com/privacy",
  "IMAGE_URL": "https://zevenglobal.com/images",

  "EMAIL_BG_COLOR": "#f0f5ff",
  "CONTAINER_BG_COLOR": "#0a1a35",
  "HEADER_BG_COLOR": "#0a1730",
  "HERO_BG_COLOR": "#101f3d",
  "FOOTER_BG_COLOR": "#0a1730",
  "CARD_BG_COLOR": "rgba(18, 37, 73, 0.9)",
  "TICKET_BG_COLOR": "rgba(18, 37, 73, 0.8)",

  "ACCENT_COLOR": "#27ae60",
  "SECONDARY_TEXT_COLOR": "#b4c9ff",
  "LABEL_COLOR": "#27ae60",
  "FOOTER_TEXT_COLOR": "#d1d5db",
  "STATUS_COLOR": "#27ae60",
  "STATUS_BG_COLOR": "rgba(39, 174, 96, 0.1)",

  "SHADOW_COLOR": "rgba(0, 65, 158, 0.2)",
  "BORDER_COLOR": "rgba(100, 150, 255, 0.2)",
  "CARD_BORDER_COLOR": "rgba(39, 174, 96, 0.3)",
  "DIVIDER_COLOR": "rgba(39, 174, 96, 0.2)",

  "HIGHLIGHT_COLOR": "rgba(39, 174, 96, 0.2)",
  "HIGHLIGHT_BG_COLOR": "rgba(39, 174, 96, 0.05)",
  "WARNING_COLOR": "#27ae60",
  "WARNING_BG_COLOR": "rgba(39, 174, 96, 0.1)",

  "SOCIAL_LINKS": {
    "facebook": "https://facebook.com/zevenglobal",
    "twitter": "https://twitter.com/zevenglobal",
    "instagram": "https://instagram.com/zevenglobal"
  }
}
```

## Instrucciones de uso en n8n

1. Crea un nodo de tipo "Global Constants" en tu flujo de trabajo
2. Copia uno de los bloques JSON anteriores según la empresa para la que estás configurando los correos
3. Pega el JSON en la propiedad "json" del nodo Global Constants
4. Referencia estas variables en los templates HTML usando la sintaxis: `{{ $('Global Constants').item.json.constants.NOMBRE_VARIABLE }}`

## Tipos de templates disponibles

Los siguientes templates están disponibles en la carpeta `/templates`:

1. **buy_challenge_template.html** - Correo de confirmación de compra de challenge
2. **approved_challenge_template.html** - Correo de aprobación de challenge
3. **disapproved_challenge_template.html** - Correo de desaprobación de challenge
4. **missing_broker_template.html** - Correo de notificación de cuenta de broker faltante
5. **buy_ticket_template.html** - Correo de confirmación de compra de ticket
6. **reset_password_template.html** - Correo para reseteo de contraseña o verificación de email

Para cada template, asegúrate de tener configurados los nodos adecuados en n8n que proporcionen los datos necesarios como challenge_type, account_size, etc. según corresponda para cada plantilla.
