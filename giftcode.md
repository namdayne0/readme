# GiftCode Plugin

**Author:** Namdev  
**Version:** 1.0.0  
**Compatibility:** Minecraft 1.16 - 1.21.8  

Advanced GiftCode plugin for Minecraft servers that allows administrators to create and manage gift codes with items, usage limits, and expiry times.

## 🎁 Features

- **Create Gift Codes**: Create custom gift codes with unique names
- **GUI Item Editor**: 27-slot GUI menu for adding/editing items in gift codes
- **Usage Limits**: Set how many players can use each gift code
- **Expiry Times**: Set expiration dates for gift codes (supports: seconds, minutes, hours, days, weeks, years)
- **Player Tracking**: Track which players have used each gift code
- **Auto-Save**: Automatic saving of gift code data
- **Permissions**: Full permission system for admin and user commands
- **Multi-Version Support**: Works on Minecraft 1.16 to 1.21.8

## 📦 Installation

1. Download the plugin JAR file
2. Place it in your server's `plugins` folder
3. Restart your server
4. The plugin will create default configuration files automatically

## 🔧 Building from Source

Requirements:
- Java 8 or higher
- Maven 3.6+

```bash
git clone <repository-url>
cd giftcode-plugin
mvn clean package
```

The compiled JAR will be in the `target` folder.

## 📋 Commands

### Admin Commands (`/giftcode`)
**Permission:** `giftcode.admin`

- `/giftcode create <code>` - Create a new gift code
- `/giftcode edit <code>` - Open GUI to edit gift code items
- `/giftcode limit <code> <amount>` - Set usage limit for a gift code
- `/giftcode settime <code> <time>` - Set expiry time for a gift code
- `/giftcode remove <code>` - Remove a gift code
- `/giftcode list` - List all gift codes
- `/giftcode info <code>` - Show detailed information about a gift code
- `/giftcode reload` - Reload the plugin configuration
- `/giftcode help` - Show command help

### Player Commands (`/code`)
**Permission:** `giftcode.use` (default: true)

- `/code <gift-code>` - Redeem a gift code to receive items

## ⏰ Time Formats

When setting expiry times, use these formats:

- `s` - seconds (e.g., `30s` = 30 seconds)
- `m` - minutes (e.g., `5m` = 5 minutes) 
- `h` - hours (e.g., `2h` = 2 hours)
- `d` - days (e.g., `3d` = 3 days)
- `w` - weeks (e.g., `1w` = 1 week)
- `y` - years (e.g., `1y` = 1 year)

**Examples:**
- `/giftcode settime WELCOME123 1d` - Expires in 1 day
- `/giftcode settime EVENT2024 7d` - Expires in 1 week
- `/giftcode settime SPECIAL 2h` - Expires in 2 hours

## 🛡️ Permissions

- `giftcode.*` - All permissions
- `giftcode.admin` - Access to admin commands (default: op)
- `giftcode.use` - Ability to redeem gift codes (default: true)

## 🎮 Usage Examples

### Creating a Gift Code
1. `/giftcode create WELCOME123` - Creates the gift code
2. `/giftcode edit WELCOME123` - Opens GUI menu to add items
3. Place items in the GUI slots (first 21 slots)
4. Click the "Save" button or close the menu to save

### Setting Limits and Expiry
```
/giftcode limit WELCOME123 50        # Allow 50 uses
/giftcode settime WELCOME123 7d      # Expires in 7 days
```

### Player Redemption
Players use: `/code WELCOME123` to redeem the gift code

## 📁 GUI Menu

The editing menu has 27 slots:
- **Slots 0-20**: Item slots (place your reward items here)
- **Slot 21**: Glass pane (decoration)
- **Slot 22**: Save button (emerald)
- **Slot 23**: Clear button (red concrete)
- **Slot 24**: Info button (book) - shows gift code information
- **Slot 25**: Cancel button (barrier)
- **Slot 26**: Glass pane (decoration)

## 💾 Data Storage

The plugin stores data in:
- `plugins/GiftCode/config.yml` - Configuration file
- `plugins/GiftCode/giftcodes.yml` - Gift code data

## 🔄 API Usage

Developers can integrate with the plugin:

```java
GiftCodePlugin plugin = (GiftCodePlugin) Bukkit.getPluginManager().getPlugin("GiftCode");
GiftCodeManager manager = plugin.getGiftCodeManager();

// Create a gift code
manager.createGiftCode("TESTCODE");

// Add items programmatically
GiftCode giftCode = manager.getGiftCode("TESTCODE");
giftCode.addItem(new ItemStack(Material.DIAMOND, 5));

// Save changes
manager.saveData();
```

## 🐛 Troubleshooting

### Plugin not loading
- Check that you have Java 8+ 
- Verify Minecraft version compatibility (1.16-1.21.8)
- Check console for error messages

### Commands not working
- Verify permissions are set correctly
- Check that the plugin is enabled: `/plugins`

### GUI not opening
- Ensure you're using the command as a player, not console
- Check for inventory plugin conflicts

## 📝 Configuration

The `config.yml` file contains various settings including:
- Custom messages
- Auto-cleanup settings  
- GUI configurations
- Storage options

## 🤝 Support

For support, bug reports, or feature requests:
- Check the documentation
- Report issues with detailed information
- Include server version and plugin version

## 📜 License

This plugin is created by **Namdev**. 
Please do not redistribute without permission.

## 🎯 Version History

- **v1.0.0** - Initial release
  - Basic gift code creation and management
  - GUI item editor with 27 slots
  - Usage limits and expiry times
  - Full command system
  - Multi-version support (1.16-1.21.8)
