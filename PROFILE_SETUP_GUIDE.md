# Muhammad Waqas - Personal Profile Website Setup Guide

## Overview
A comprehensive single-page personal profile website for .NET developers with vibrant, colorful design using Bootstrap 5 and custom CSS.

## Features Included

### Sections:
1. **Navigation Bar** - Sticky navigation with smooth scrolling
2. **Hero Section** - Eye-catching introduction with call-to-action buttons
3. **About Section** - Professional introduction with statistics
4. **Skills Section** - Technical skills with proficiency bars and categorization
5. **Experience Section** - Timeline view of professional journey
6. **Projects Section** - Featured project showcase with descriptions
7. **Certifications** - Professional certifications and achievements
8. **Contact Section** - Contact information and message form with social links
9. **Responsive Footer** - Professional footer with copyright

### Design Features:
- ✅ Vibrant gradient color schemes (Purple, Pink, Cyan, Orange)
- ✅ Smooth animations and transitions
- ✅ Hover effects on all interactive elements
- ✅ Fully responsive (mobile, tablet, desktop)
- ✅ Modern Bootstrap 5 framework
- ✅ Scroll animations for cards and sections
- ✅ Sticky navigation bar

## Installation & Setup

### Step 1: Create a WordPress Page
1. Go to WordPress Admin Dashboard → **Pages → Add New**
2. Give it a title: "Profile" or "About Me"
3. Set the page slug to: `profile`
4. In the page editor, select the template:
   - Find the "Template" option in the right sidebar
   - Select **"Personal Profile"** from the dropdown
5. Click **Publish**

### Step 2: Access Your Profile Page
- Visit: `http://yoursite.com/profile/`
- The page will automatically use the custom template

## Customization Guide

### Update Personal Information

#### Edit in: `page-profile.php`

**Name & Title** (Line ~90-95):
```php
<h1 class="display-3 fw-bold mb-4 text-white">Muhammad Waqas</h1>
<h2 class="h3 mb-4 text-white-50">Full-Stack .NET Developer & WordPress Specialist</h2>
```

**About Section** (Line ~175-185):
```php
<p class="lead mb-3">Update your professional introduction here</p>
```

**Contact Information** (Line ~450-480):
- Email
- Phone Number
- Location

**Social Media Links** (Line ~490-510):
Update the href attributes with your actual profiles:
```php
<a href="https://linkedin.com/in/yourprofile" target="_blank">
```

### Customize Skills

**Skill Categories** (Lines ~245-315):
Add or edit the three main skill cards:
- Backend Development (C#, .NET)
- Frontend Development (HTML, CSS, JS)
- E-Commerce & CMS (WordPress, WooCommerce)

**Proficiency Bars** (Lines ~325-365):
Add or edit skill proficiency bars with custom percentages

### Update Experience Timeline

**Timeline Items** (Lines ~385-425):
Modify experience entries:
```php
<h4>Your Job Title</h4>
<span class="text-muted">2020 - Present</span>
<p class="mt-2">Your job description here</p>
```

### Add/Edit Projects

**Featured Projects** (Lines ~445-510):
Each project card includes:
- Icon/background gradient
- Project title
- Description
- Technology badges

### Edit Certifications

**Certification Cards** (Lines ~525-560):
```php
<h4>Your Certification Name</h4>
<p class="text-muted mb-2">Issuing Organization | Year</p>
```

## Color Customization

### CSS Variables (in `profile-style.css`):
```css
:root {
    --primary-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    --secondary-gradient: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
    --tertiary-gradient: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
}
```

### Color Schemes:
- **Purple**: `#667eea` - `#764ba2` (Primary)
- **Pink**: `#f093fb` - `#f5576c` (Secondary)
- **Cyan**: `#4facfe` - `#00f2fe` (Tertiary)
- **Orange**: `#fa709a` - `#fee140` (Accent)

To change colors, update the gradient values in the CSS root variables.

## Adding a Contact Form

The contact form is ready to use with WordPress AJAX. To enable email notifications:

1. Add this to your theme's `functions.php`:
```php
add_action('wp_ajax_nopriv_profile_contact', 'profile_handle_contact');
add_action('wp_ajax_profile_contact', 'profile_handle_contact');

function profile_handle_contact() {
    $name = sanitize_text_field($_POST['contact_name']);
    $email = sanitize_email($_POST['contact_email']);
    $subject = sanitize_text_field($_POST['contact_subject']);
    $message = sanitize_textarea_field($_POST['contact_message']);
    
    $to = get_option('admin_email');
    $headers = "From: " . $email;
    
    wp_mail($to, "New Profile Message: " . $subject, $message, $headers);
    wp_die('Email sent successfully!');
}
```

## Mobile Responsiveness

The template is fully responsive and includes:
- Mobile-first design approach
- Optimized layouts for tablets (768px)
- Optimized layouts for mobile (576px)
- Touch-friendly buttons and links
- Hamburger navigation menu on mobile

## SEO Optimization

Add this to the page front matter for better SEO:
1. Page Title: "Muhammad Waqas - Full-Stack .NET Developer"
2. Meta Description: "Professional profile of Muhammad Waqas, experienced .NET developer specializing in ASP.NET Core and WordPress e-commerce solutions."
3. Focus Keywords: .NET Developer, WordPress Specialist, E-Commerce

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Mobile browsers (iOS Safari, Chrome Android)

## Performance Tips

1. **Optimize Images**: Compress any profile images before uploading
2. **Enable Caching**: Use a caching plugin like WP Super Cache
3. **Lazy Loading**: Browser automatically lazy-loads images
4. **Minify CSS**: Consider minifying the CSS file in production

## Troubleshooting

### Template Not Appearing
- Ensure file is in: `wp-content/themes/twentytwentyfive/`
- Check filename: `page-profile.php` (must be exact)
- Verify page slug is `profile`

### Styles Not Loading
- Check that CSS file path is correct
- Clear browser cache (Ctrl+Shift+Delete)
- Ensure theme directory exists

### Contact Form Not Working
- Verify WordPress AJAX is enabled
- Check that form method is POST
- Ensure admin_email is configured in WordPress settings

## File Locations

```
wp-content/themes/twentytwentyfive/
├── page-profile.php          (Main template)
└── css/
    └── profile-style.css     (Custom styles)
```

## Future Enhancements

Consider adding:
- Blog section with recent posts
- Testimonials from clients
- Newsletter subscription
- Dark mode toggle
- Multilingual support
- Photo gallery
- Resume download button
- Video introduction

## Support & Updates

For updates or custom features, reach out to your developer.

---

**Created:** 2024
**Version:** 1.0
**Compatibility:** WordPress 6.0+ with Twenty Twenty-Five theme
