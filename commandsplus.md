# CommandPlus Plugin

![Version](https://img.shields.io/badge/version-1.0.0-green)
![Minecraft](https://img.shields.io/badge/minecraft-1.16+-blue)
![Author](https://img.shields.io/badge/author-NamDev-red)

Một plugin quản lý commands động cho Minecraft server, cho phép thêm custom commands thông qua file YAML mà không cần restart server.

## Tác giả
- **NamDev** - [GitHub](https://github.com/namdayne0)

## Tính năng

### ✨ Custom Commands
- Tạo commands tùy chỉnh thông qua file `commands.yml`
- Hỗ trợ aliases cho commands
- Phân quyền chi tiết cho từng command
- Thực hiện actions: console, player, broadcast

### 🔄 Hot Reload
- Reload commands mà không cần restart server
- Lệnh `/cp reload` để tải lại cấu hình
- Thời gian reload nhanh chóng

### 🚫 Block Commands
- Chặn các lệnh nguy hiểm
- Thông báo lỗi tùy chỉnh khi lệnh bị chặn
- Ngăn chặn cả từ player và console

### 🎨 Tùy chỉnh
- Messages có thể tùy chỉnh hoàn toàn
- Hỗ trợ color codes (&a, &c, &l, v.v.)
- Placeholder %player% cho tên người chơi

## Cài đặt

1. Download file `.jar` của plugin
2. Đặt vào thư mục `plugins/` của server
3. Restart server
4. File `commands.yml` sẽ được tạo tự động trong `plugins/CommandPlus/`

## Cấu trúc thư mục

```
server/
├── plugins/
│   ├── CommandPlus.jar
│   └── CommandPlus/
│       └── commands.yml
```

## Cách sử dụng

### Format cho Custom Commands

```yaml
commands:
  - "command [alias1,alias2] permission:perm action:type/value"
```

**Các thành phần:**
- `command`: Tên lệnh chính
- `[alias1,alias2]`: Aliases (có thể bỏ qua)
- `permission:perm`: Quyền cần thiết (mặc định: commandplus.use)
- `action:type/value`: Hành động thực hiện

### Các loại Actions

| Action Type | Mô tả | Ví dụ |
|------------|-------|--------|
| `console/command` | Chạy lệnh từ console | `action:console/heal %player%` |
| `player/command` | Chạy lệnh từ player | `action:player/fly` |
| `broadcast/message` | Broadcast tin nhắn | `action:broadcast/&aWelcome!` |

### Ví dụ Commands

```yaml
commands:
  # Lệnh heal với aliases
  - "heal [h,hp] permission:commandplus.heal action:console/heal %player%"
  
  # Lệnh fly
  - "fly [f] permission:commandplus.fly action:console/fly %player%"
  
  # Gamemode creative
  - "gmc permission:commandplus.gm action:console/gamemode creative %player%"
  
  # Broadcast message
  - "hello action:broadcast/&a[Server] &fWelcome %player%!"
```

### Block Commands

```yaml
block-commands:
  - "op"
  - "deop" 
  - "stop"
  - "whitelist"
```

## Lệnh plugin

### `/commandplus` hoặc `/cp`
**Quyền:** `commandplus.admin`

- `/cp` - Hiển thị thông tin plugin
- `/cp reload` - Reload commands từ file

## Permissions

| Permission | Mô tả | Mặc định |
|-----------|--------|----------|
| `commandplus.admin` | Truy cập lệnh admin | OP |
| `commandplus.use` | Sử dụng custom commands | true |
| `commandplus.heal` | Sử dụng lệnh heal | OP |
| `commandplus.fly` | Sử dụng lệnh fly | OP |
| `commandplus.gm` | Sử dụng gamemode | OP |

## File cấu hình mẫu

```yaml
# CommandPlus Configuration File
commands:
  - "heal [h,hp] permission:commandplus.heal action:console/heal %player%"
  - "fly [f] permission:commandplus.fly action:console/fly %player%"
  - "gmc permission:commandplus.gm action:console/gamemode creative %player%"

block-commands:
  - "op"
  - "deop"
  - "stop"

messages:
  blocked-command: "&c&l[!] &cLệnh này đã bị chặn!"
  no-permission: "&c&l[!] &cBạn không có quyền!"
  reload-success: "&a&l[✓] &aReload thành công!"

settings:
  show-execution-message: false
  log-commands: true
  enable-placeholders: true
  message-prefix: "&8[&bCommandPlus&8]&r "
```

## Placeholders

- `%player%` - Tên người chơi thực hiện lệnh

## Color Codes

Hỗ trợ tất cả color codes của Minecraft:
- `&0-&9` - Màu sắc
- `&a-&f` - Màu sắc
- `&l` - Bold
- `&o` - Italic
- `&n` - Underline
- `&m` - Strikethrough
- `&k` - Magic
- `&r` - Reset

## Troubleshooting

### Plugin không load
- Kiểm tra version Minecraft (cần 1.16+)
- Xem log server để tìm lỗi

### Commands không hoạt động
- Kiểm tra syntax trong `commands.yml`
- Sử dụng `/cp reload` sau khi sửa file
- Kiểm tra permissions

### File commands.yml bị lỗi
- Xóa file và restart server để tạo lại file mặc định
- Kiểm tra indentation (dùng spaces, không dùng tabs)

## Changelog

### v1.0.0
- ✨ Release đầu tiên
- ✅ Custom commands với aliases
- ✅ Hot reload functionality  
- ✅ Block commands system
- ✅ Permission system
- ✅ Color codes support
- ✅ Placeholder system

## License

MIT License - Xem file LICENSE để biết thêm chi tiết.

---

**Made with ❤️ by NamDev**
