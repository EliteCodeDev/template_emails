# Templates de Correo Electrónico para N8N

Este proyecto contiene templates HTML de correo electrónico diseñados para ser utilizados con n8n. Los templates están configurados para recibir datos y colores dinámicamente a través del flujo de trabajo de n8n.

## Estructura del Proyecto

```
/templates
├── approved_challenge_template.html     # Template para correos de challenge aprobado
├── buy_challenge_template.html          # Template para correos de compra de challenge
├── buy_ticket_template.html             # Template para correos de compra de ticket
├── color_variables.md                   # Variables de configuración de colores y otros ajustes
├── disapproved_challenge_template.html  # Template para correos de challenge desaprobado
├── missing_broker_template.html         # Template para correos de broker faltante
└── reset_password_template.html         # Template para correos de reseteo/verificación
```

## Cómo Usar los Templates

1. **Configurar Global Constants en n8n**:

   - Crea un nodo de "Global Constants" en tu flujo de trabajo
   - Copia uno de los bloques JSON del archivo `color_variables.md` según la empresa
   - Pega el JSON en la propiedad "json" del nodo Global Constants

2. **Preparar los datos necesarios**:

   - Configura nodos en n8n que proporcionen los datos necesarios para cada template
   - Por ejemplo, para `buy_challenge_template.html` necesitarás un nodo llamado "Challenge Details" con datos como challenge_type, account_size, etc.

3. **Utilizar el template en un nodo HTML**:

   - Crea un nodo HTML en n8n
   - Copia y pega el contenido del template correspondiente
   - Asegúrate de que las referencias a los datos en el template coincidan con los nombres de tus nodos en n8n

4. **Referencias a las variables**:
   - Variables globales: `{{ $('Global Constants').item.json.constants.NOMBRE_VARIABLE }}`
   - Datos dinámicos: `{{ $node["Challenge Details"].json.nombre_propiedad }}`

## Personalización de Colores

Los templates están diseñados para ser completamente personalizables en términos de colores y estilos. Todas las variables de color están definidas en el archivo `color_variables.md` y se proporcionan dos configuraciones predeterminadas:

1. **Neocapital**: Esquema de colores oscuros con acentos en tonos naranja/amber
2. **ZevenGlobal**: Esquema de colores oscuros con acentos en tonos azules/verdes

Para modificar los colores, simplemente actualiza las variables en el nodo "Global Constants" de tu flujo de trabajo.

## Datos Requeridos por Template

### reset_password_template.html

```json
{
  "email_subject": "Reset Your Password",
  "greeting": "Hello dear one 👋",
  "intro_message": "We received a request to reset your password.",
  "main_message": "To set a new password, please click the button below:",
  "button_text": "Reset Password",
  "action_url": "https://example.com/reset-password?token=abc123",
  "closing_message": "Thank you for using our platform.",
  "show_verification_code": true,
  "verification_code": "123456",
  "expiry_time": "24 hours"
}
```

### buy_challenge_template.html

```json
{
  "challenge_type": "Standard Challenge",
  "account_size": 100000,
  "challenge_id": "CH-12345",
  "platform": "MetaTrader 5",
  "login_details": {
    "username": "trader123",
    "password": "pass123"
  },
  "dashboard_url": "https://example.com/dashboard"
}
```

### approved_challenge_template.html

```json
{
  "challenge_type": "Standard Challenge",
  "account_size": 100000,
  "challenge_id": "CH-12345",
  "profit_target": 8000,
  "dashboard_url": "https://example.com/dashboard",
  "verification_url": "https://example.com/verify",
  "profit_split": 80,
  "payout_frequency": "Monthly",
  "platform": "MetaTrader 5"
}
```

### disapproved_challenge_template.html

```json
{
  "challenge_type": "Standard Challenge",
  "account_size": 100000,
  "challenge_id": "CH-12345",
  "violated_rules": [
    "Maximum Daily Loss Exceeded",
    "Trading Outside of Permitted Hours",
    "Position Size Limit Exceeded"
  ],
  "dashboard_url": "https://example.com/dashboard",
  "discount_code": "TRY-AGAIN-20",
  "discount_percentage": 20,
  "new_challenge_url": "https://example.com/new-challenge"
}
```

### missing_broker_template.html

```json
{
  "dashboard_url": "https://example.com/dashboard"
}
```

### buy_ticket_template.html

```json
{
  "ticket_id": "TKT-12345",
  "event_name": "Trading Masterclass",
  "event_date": "May 15, 2025",
  "event_time": "2:00 PM - 5:00 PM EST",
  "event_location": "Financial Conference Center, New York",
  "ticket_type": "VIP Access",
  "attendee_name": "John Smith",
  "qr_code_url": "https://example.com/qr-code.png",
  "download_ticket_url": "https://example.com/download-ticket",
  "event_description": "Join our exclusive Trading Masterclass to learn advanced trading strategies from top industry professionals.",
  "venue_directions": "The Financial Conference Center is located in downtown New York, accessible via subway lines A, B, and C. Parking is available in the adjacent garage.",
  "additional_info": [
    "Doors open 30 minutes before the event",
    "Photo ID required for entry",
    "Refreshments will be provided",
    "Recording equipment is not permitted"
  ]
}
```

## Notas Adicionales

- Los templates son responsivos y se verán bien en dispositivos móviles y de escritorio
- Todos los templates utilizan la fuente Montserrat de Google Fonts
- Las imágenes y logotipos deben alojarse externamente y referenciarse a través de las variables correspondientes
