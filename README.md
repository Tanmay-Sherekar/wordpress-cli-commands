 **WP-CLI steps** to manage WordPress via terminal. I’ll give you a detailed, step-by-step guide from installation to common usage.

---

## **1. Install WP-CLI**

WP-CLI is a PHP-based command-line tool. Make sure PHP & WordPress are installed first.

### **Linux / macOS**

```bash
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
php wp-cli.phar --info         # Verify PHP can run it
chmod +x wp-cli.phar
sudo mv wp-cli.phar /usr/local/bin/wp
wp --info                     # Check WP-CLI is installed
```

### **Windows**

* Use **Composer** or **Windows binary**.
* Using Composer:

```bash
composer global require wp-cli/wp-cli-bundle
```

* Add Composer’s `vendor/bin` directory to your PATH.

---

## **2. Navigate to WordPress Directory**

WP-CLI must run in the folder where `wp-config.php` exists:

```bash
cd /path/to/your/wordpress
```

---

## **3. Basic WP-CLI Commands**

### **a) Check WordPress Version**

```bash
wp core version
```

### **b) Update WordPress**

```bash
wp core update
wp core update-db    # Update database if required
```

### **c) Manage Plugins**

```bash
wp plugin install plugin-slug --activate      # Install & activate
wp plugin activate plugin-slug                # Activate existing plugin
wp plugin deactivate plugin-slug              # Deactivate
wp plugin update plugin-slug                  # Update
wp plugin list                                # List all plugins
wp plugin uninstall plugin-slug               # Remove
```

### **d) Manage Themes**

```bash
wp theme install twentytwenty --activate
wp theme update twentytwenty
wp theme list
wp theme delete twentytwenty
```

### **e) Create Users**

```bash
wp user create john john@example.com --role=editor --user_pass=strongpassword
wp user list
wp user delete 5 --reassign=1   # Delete user ID 5, reassign posts to user ID 1
```

### **f) Manage Posts**

```bash
wp post create --post_type=post --post_title="Hello WP-CLI" --post_status=publish
wp post list
wp post delete 10 --force
```

### **g) Database Operations**

```bash
wp db create        # Create DB (if wp-config.php set)
wp db drop --yes     # Drop DB
wp db export         # Export SQL
wp db import file.sql
wp db optimize
wp db repair
```

### **h) Search & Replace**

```bash
wp search-replace 'http://old-url.com' 'https://new-url.com' --dry-run
wp search-replace 'http://old-url.com' 'https://new-url.com'
```

### **i) Backup / Restore**

WP-CLI doesn’t have a built-in backup command, but you can combine:

```bash
wp db export backup.sql
```

Then restore:

```bash
wp db import backup.sql
```

### **j) Cron & Cache**

```bash
wp cron event list
wp cron event run publish_future_posts
wp cache flush
```

---

## **4. Handy Tips**

* Add `--allow-root` if running as root (not recommended for production).
* Combine with `&&` to automate multiple steps:

```bash
wp core update && wp plugin update --all && wp theme update --all
```

* Use `wp help` for full command reference.


Do you want me to do that?
