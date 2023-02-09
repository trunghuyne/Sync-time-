- Đồng bộ hóa ngày openwrt bằng cách chọn ngày từ miền đã chọn.
- Đồng bộ hóa thời gian trong OpenWrt bằng cách lấy dữ liệu thời gian từ miền đã chọn.
- Hỗ trợ đồng bộ thời gian khi có kết nối modem/internet.
- Trình kiểm tra kết nối (nếu sử dụng chế độ cron, tập lệnh sẽ kiểm tra kết nối, sau đó khởi động lại ứng dụng VPN nếu không có kết nối internet)
- Cài đặt múi giờ tự động tuân theo LuCI - System - System - Timezone.
- Hỗ trợ cài đặt múi giờ cho VPN:
    - OpenClash
    - Passwall
    - ShadowsocksR
    - ShadowsocksR++
    - v2ray
    - v2rayA
    - xray
    - Libernet
    - Xderm Mini
    - Wegare STL

### Sử dụng mặc định - Sử dụng cơ bản
Cài đặt các gói yêu cầu trước bằng cách mở terminal:
    ```
    opkg update && opkg install curl wget httping
    ```

- Dán lệnh bên dưới để cài đặt tập lệnh ``uptime-openwrt``
- Dùng wget:

    ```
    wget --no-check-certificate "https://raw.githubusercontent.com/thangnguyencl/Sync-time-/main/times-openwrt" -O /usr/bin/times-openwrt && chmod +x /usr/bin/times-openwrt
    ```
    
 - dùng curl:
    
    ```
    curl -sL https://raw.githubusercontent.com/thangnguyencl/Sync-time-/main/times-openwrt > /usr/bin/times-openwrt && chmod +x /usr/bin/times-openwrt
    ```
- Nhập lệnh bên dưới vào LuCI -> System -> Startup -> Local Startup hoặc tại rc.local nếu ở trong terminal
- Ví dụ dùng mạng Viettel:

    ```
    /usr/bin/times-openwrt m.tv360.vn
    ```

- Nếu sử dụng crontab (kiểm tra kết nối cứ sau 1 giờ, sau đó khởi động lại vpn nếu không có kết nối), sao chép lệnh bên dưới vào LuCI -> System -> Schedule Tasks Ví dụ:
    ```
    0 * * * * /usr/bin/times-openwrt m.tv360.vn cron
    ```

    - Lệnh trên cũng có thể được bao gồm trong tệp/etc/crontabs/root
    - Đối với các tùy chỉnh thời gian định kỳ khác, hãy xem [crontab.guru](https://crontab.guru/#0_*_*_*_*)

- Để update tập lệnh hãy thực hiện lệnh bên dưới:

    ```
    /usr/bin/times-openwrt update
    ```
    Tanda update berhasil adalah seperti ini:
    ```
    times-openwrt: Update tệp lệnh...
    times-openwrt: Đang tải tệp lệnh...
    times-openwrt: update thành công.
    times-openwrt: Đã xóa tệp update!
    Cách dùng: Thêm tên miền sau tệp lệnh!.
    times-openwrt: Thiếu tên miền/URL!. Vào inbox FB Nguyễn Thắng để biết thêm chi tiết.
    ```

### Đội ngũ phát triển
- Tập lệnh và codes của AlkhaNet by [Teguh Surya Mungaran](https://github.com/alkhanet26)
- Mã GMT và các mã khác của [Vito H.S](https://github.com/vitoharhari)
- Trình kiểm tra và cài đặt opkg, kiểm tra internet, vpn manager, codes chọn GMT của [Helmi Amirudin](https://helmiau.com)
