# Learnshapes LMS Plugin

**Learnshapes** is a premium, robust, and extensible Learning Management System (LMS) plugin for WordPress. It is designed to provide educators, instructors, and institutions with the tools they need to build, manage, and sell online courses with ease.

## 🚀 Features

- **Intuitive Curriculum Builder**: Drag-and-drop course, lesson, and quiz builder to structure your curriculum seamlessly.
- **Student & Instructor Dashboards**: Dedicated frontend dashboards for students to track progress and for instructors to manage courses.
- **Robust Payment Gateways**: Built-in support for WooCommerce, PayPal, Stripe, and Offline payments.
- **Advanced Quizzing**: Interactive quiz modules with dynamic scoring, multiple question types, and immediate feedback.
- **Extensible Architecture**: Developer-friendly structure with comprehensive Hooks, Filters, and REST API support.
- **Responsive UI/UX**: Premium, distraction-free learning experience tailored for any screen size.

## 📁 Directory Structure

```text
learnshapes/
├── assets/                  # CSS, JS, and Images for frontend and admin
├── includes/                # Core PHP classes and logic
│   ├── Admin/               # Backend settings and administrative panels
│   ├── Core/                # Base plugin structure (Assets, Setup, Plugin initialization)
│   ├── Payments/            # Payment gateway architecture (PayPal, Stripe, etc.)
│   ├── REST/                # Custom REST API endpoints for dynamic frontend data
│   ├── Shortcodes/          # Logic for frontend rendering (Dashboards, Course grids)
│   └── Blocks/              # Gutenberg Block Registry
├── templates/               # Overridable frontend template files
│   ├── course/              # Single course, grid, and player templates
│   ├── dashboard/           # Student and Instructor dashboard templates
│   ├── checkout/            # Checkout flows and order receipts
│   └── emails/              # HTML email templates for notifications
├── learnshapes.php          # Main plugin file
└── README.md                # This file
```

## 🛠️ Installation

1. Upload the `learnshapes` folder to the `/wp-content/plugins/` directory of your WordPress installation.
2. Activate the plugin through the 'Plugins' menu in WordPress.
3. Navigate to **Learnshapes > Settings** in the WordPress admin menu to configure your payment gateways, pages, and general preferences.

## 🎨 Template Overrides

Learnshapes allows you to customize its frontend templates without touching the core plugin files. 

To override a template:
1. Create a folder named `learnshapes` within your active theme's root directory.
2. Copy the template file you wish to modify from the plugin's `/templates/` directory.
3. Paste it into your theme's `learnshapes` folder, maintaining the identical folder structure.

*Example:* 
To override `/wp-content/plugins/learnshapes/templates/course/single-course.php`, copy it to `/wp-content/themes/your-theme/learnshapes/course/single-course.php`.

## 📌 Shortcodes

Learnshapes provides several shortcodes to display dynamic content anywhere on your site:

- `[learnshapes_courses]` - Displays the standard courses grid.
- `[learnshapes_my_courses]` - Displays the courses enrolled by the current user.
- `[learnshapes_student_dashboard]` - Renders the full student dashboard.
- `[learnshapes_instructor_dashboard]` - Renders the instructor management dashboard.
- `[learnshapes_checkout]` - Renders the Learnshapes standalone checkout form.

## 👨‍💻 Developer API (Hooks & Filters)

Learnshapes is built with extensibility in mind, allowing developers to hook into the enrollment, payment, and progress tracking lifecycle.

### Action Hooks (`do_action`)

**Courses & Enrollment:**
- `learnshapes_course_builder_saved` - Fires when the curriculum structure is saved.
- `learnshapes_before_course_enroll` - Fires immediately before a user is enrolled in a course.
- `learnshapes_after_course_enroll` - Fires immediately after a successful enrollment.
- `learnshapes_after_{$item_type}_complete` - Fires when a lesson or topic is completed.
- `learnshapes_after_course_complete` - Fires when all items in a course are marked complete.

**Quizzes & Assignments:**
- `learnshapes_after_quiz_submit` - Fires when a user submits a quiz.
- `learnshapes_after_assignment_submit` - Fires when an assignment is uploaded.
- `ls_assignment_graded` - Fires when an instructor grades an assignment.
- `ls_certificate_issued` - Fires when a student earns a certificate.

**Payments & Orders:**
- `learnshapes_before_order_create` - Fires before a new order record is inserted.
- `learnshapes_order_created` - Fires after an order is successfully created.
- `learnshapes_order_status_changed` - Fires when an order status shifts (e.g., from pending to completed).
- `learnshapes_order_{$status}` - Dynamic hook for specific order statuses.
- `learnshapes_payment_checkout_fields` - Allows adding custom fields to the checkout form.
- `learnshapes_payment_success` - Fires upon successful payment verification.
- `learnshapes_payment_failure` - Fires when a payment fails or is rejected.

### Filters (`apply_filters`)

**Gateways & Checkout:**
- `learnshapes_payment_gateways` - Filter the array of registered payment gateways to add/remove providers.
- `learnshapes_gateway_title` - Modify the display title of a payment gateway.
- `learnshapes_gateway_description` - Modify the description of a payment gateway.
- `learnshapes_validate_checkout_fields_{$gateway_id}` - Add custom validation rules for checkout fields.
- `learnshapes_paypal_args` - Filter the arguments sent to PayPal during redirect.
- `learnshapes_offline_initial_order_status` - Modify the default starting status for offline payments.

*(See the `includes/REST/API.php` and `includes/Payments/GatewayManager.php` files for more context on hook arguments.)*

## ⚙️ Requirements

- WordPress 6.0+
- PHP 8.1+
- MySQL 5.7+ / MariaDB 10.3+

## 📄 License

This plugin is proprietary software. All rights reserved.
