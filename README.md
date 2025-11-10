# Educare Connect - Authentication Pages

Landing pages for email authentication redirects in the Educare Connect mobile application.

## 🎯 Purpose

This repository hosts static HTML pages that handle email confirmation, password reset, and email change flows for the Educare Connect React Native application. When users click links in authentication emails, they're directed to these pages which then redirect back to the mobile app with the appropriate tokens.

## 🔗 Supported Flows

- **Email Confirmation** (`?type=signup`) - Confirms new user registration
- **Password Reset** (`?type=recovery`) - Handles password reset requests
- **Email Change** (`?type=email_change`) - Confirms email address changes

## 🚀 Live URL

The pages are hosted at: `https://YOUR_USERNAME.github.io/educare-auth-pages/`

## 📱 How It Works

1. User performs an action in the mobile app (sign up, reset password, change email)
2. Supabase sends an authentication email with a link to this page
3. User clicks the link, which opens in their browser
4. This page validates the tokens and displays status
5. Page automatically redirects to the mobile app via deep link
6. Mobile app receives tokens and completes the authentication flow

## 🔧 Deep Link Scheme

The mobile app uses the custom URL scheme: `educareconnect://`

### Deep Link Format

```
educareconnect://auth/[action]?access_token=[TOKEN]&refresh_token=[TOKEN]
```

**Actions:**

- `confirmed` - After successful email confirmation
- `reset-password` - After clicking password reset link
- `email-changed` - After confirming new email

## 🛠️ Setup for Development

### Prerequisites

- GitHub account
- Supabase project
- Educare Connect React Native app with deep linking configured

### Configuration Steps

1. **Fork/Clone this repository**

   ```bash
   git clone https://github.com/YOUR_USERNAME/educare-auth-pages.git
   ```

2. **Enable GitHub Pages**

   - Go to repository Settings → Pages
   - Set Source to `main` branch, `root` folder
   - Save and note your GitHub Pages URL

3. **Configure Supabase**

   - Add your GitHub Pages URL to allowed redirect URLs
   - Update email templates to use your URL
   - See [SETUP_GUIDE.md](./SETUP_GUIDE.md) for detailed instructions

4. **Update Mobile App**
   - Configure deep linking for `educareconnect://` scheme
   - Implement handlers for authentication callbacks
   - See integration guide in SETUP_GUIDE.md

## 📂 Repository Structure

```
.
├── index.html          # Main authentication handler page
├── README.md           # This file
└── SETUP_GUIDE.md      # Detailed setup instructions
```

## 🔒 Security

- All token passing is done via secure HTTPS
- Tokens are never stored in browser storage
- Tokens are immediately passed to the mobile app via deep link
- Pages implement proper error handling for invalid/expired tokens

## 🎨 Customization

To customize the branding:

1. Edit `index.html`
2. Update colors in the `<style>` section
3. Modify logo, text, and messaging
4. Commit and push changes
5. GitHub Pages will automatically deploy updates

## 📱 Browser Compatibility

- iOS Safari 12+
- Android Chrome 70+
- Desktop browsers (for testing)

## 🐛 Troubleshooting

### Link doesn't redirect to app

- Verify deep linking is properly configured in mobile app
- Check that URL scheme matches: `educareconnect://`
- Test deep link manually in Safari/Chrome

### "Invalid redirect URL" error

- Ensure your GitHub Pages URL is added to Supabase allowed URLs
- Check for typos in URL configuration
- Remove trailing slashes from URLs

### Email not received

- Check spam folder
- Verify email is confirmed in Supabase dashboard
- For production, configure custom SMTP server

## 📄 License

This project is part of the Educare Connect application ecosystem.

© 2025 Educare Connect. All rights reserved.

## 📞 Support

For issues or questions:

- Email: support@educareconnect.com
- Documentation: See SETUP_GUIDE.md

---

**Note:** This is a companion repository to the main Educare Connect mobile application. It should not be used independently.
