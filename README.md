/NITRO/ API Documentation
Overview
The /NITRO/ endpoint provides detailed information about a VPN service for a specific user. It processes base64-encoded data, decodes it, and returns information about the VPN service based on the user's configuration.

فارسی
بررسی اجمالی
مسیر /NITRO/ اطلاعات دقیقی درباره سرویس VPN برای یک کاربر خاص ارائه می‌دهد. این نقطه پایان داده‌های کدگذاری‌شده به فرمت base64 را پردازش کرده، آن‌ها را دیکد کرده و اطلاعات مربوط به سرویس VPN را بر اساس پیکربندی کاربر برمی‌گرداند.

Request
URL
sql
Copy code
GET /NITRO/
Query Parameters
data (required): یک رشته کدگذاری‌شده به فرمت base64 که شامل داده‌های JSON است. داده‌های JSON باید شامل فیلدهای زیر باشد:
svid (int): شناسه سرور.
uuid (str): پسورد یا هش پیکربندی.
path (str): نام ربات یا سرویس مورد نظر.
userid (int): شناسه کاربری تلگرام مشتری.
protocol (str): پروتکل VPN.
username (str): نام کاربری پیکربندی شده مشتری.
مثال درخواست
http
Copy code
GET /NITRO/?data=eyJzdmVkIjogMSwgInV1aWQiOiAicXNoZ2VyancyYm5vZ2VyIiwgInBhdGgiOiAiTklUUk8iLCAidXNlcmlkIjogMTIzNDU2Nzg5LCAicHJvdG9jb2wiOiAiaHR0cHM6Ly9leGFtcGxlLmNvbSIsICJ1c2VybmFtZSI6ICJNeVVzZXIiIH0=
Response
Success Response
Status Code: 200 OK

json
Copy code
{
  "result": true,
  "data": {
    "downloads": 0, 
    "ex_days": 1728057531000, 
    "link": "vmess://ewogICAgInYiOiAiMiIsCiAgICAicHMiOiAiTml0cm8tMkJTNiIsCiAgICAiYWRkIjogIm5ldC5wYXljaGVjay5zdG9yZSIsCiAgICAicG9ydCI6IDM5NjYzLAogICAgImlkIjogImE3NGVhNzEzLWM1MjktNGMwYy1iZTBiLThkN2NhYzgzNTAxMCIzCiAgICAiYWlkIjogMCwKICAgICJuZXQiOiAid3MiLAogICAgInR5cGUiOiAibm9uZSIsCiAgICAiaG9zdCI6ICIiLAogICAgInBhdGgiOiAiLyIsCiAgICAidGxzIjogIm5vbmUiCn0=", 
    "path": "NITRO", 
    "port": 39663, 
    "protocol": "vmess", 
    "remain_size": 10737418240, 
    "server_name": "\ud83c\udde9\ud83c\uddea \u0622\u0644\u0645\u0627\u0646", 
    "service_name": "10 \u06af\u06cc\u06af 1 \u06a9\u0627\u0631\u0628\u0631\u0647 (1\u0645\u0627\u0647\u0647)", 
    "service_size": 10737418240, 
    "service_time": "31 \u0631\u0648\u0632", 
    "svid": 1, 
    "svip": "net.paycheck.store", 
    "uploads": 0, 
    "user_limit": 1, 
    "userid": 264150062, 
    "username": "Nitro-2BS6", 
    "uuid": "qkhgerjqwhgrqjhwgrhqwjgrq"
  }
}
Error Response
Status Code: 400 Bad Request

json
Copy code
{
  "result": false,
  "error": "No data provided"
}
Fields Description
result (boolean)
Description: Indicates whether the request was successful. true means success, and false means failure.
Example: true
data (object)
Contains detailed information about the VPN service. The following fields are included:

downloads (integer): Amount of data downloaded.

Example: 0
ex_days (integer): Expiration timestamp of the service. This value represents the number of milliseconds since the Unix epoch.

Example: 1728057531000
link (string): The base64-encoded configuration link for the VPN.

Example: "vmess://ewogICAgInYiOiAiMiIsCiAgICAicHMiOiAiTml0cm8tMkJTNiIsCiAgICAiYWRkIjogIm5ldC5wYXljaGVjay5zdG9yZSIsCiAgICAicG9ydCI6IDM5NjYzLAogICAgImlkIjogImE3NGVhNzEzLWM1MjktNGMwYy1iZTBiLThkN2NhYzgzNTAxMCIzCiAgICAiYWlkIjogMCwKICAgICJuZXQiOiAid3MiLAogICAgInR5cGUiOiAibm9uZSIsCiAgICAiaG9zdCI6ICIiLAogICAgInBhdGgiOiAiLyIsCiAgICAidGxzIjogIm5vbmUiCn0="
path (string): The name of the requested bot or service.

Example: "NITRO"
port (integer): Port number for the VPN configuration.

Example: 39663
protocol (string): VPN protocol used.

Example: "vmess"
remain_size (integer): Remaining size of the VPN service in bytes.

Example: 10737418240 (10 GB)
server_name (string): The name of the VPN server.

Example: "🇩🇪 آلمان"
service_name (string): Name of the purchased VPN service.

Example: "10 گیگ 1 کاربره (1ماه)"
service_size (integer): Total size of the VPN service in bytes.

Example: 10737418240 (10 GB)
service_time (string): Remaining duration of the VPN service.

Example: "31 روز"
svid (integer): Server ID.

Example: 1
svip (string): IP or domain of the VPN server.

Example: "net.paycheck.store"
uploads (integer): Amount of data uploaded.

Example: 0
user_limit (integer): Number of users allowed to connect using this configuration.

Example: 1
userid (integer): Telegram user ID of the customer.

Example: 264150062
username (string): Configuration username of the customer.

Example: "Nitro-2BS6"
uuid (string): UUID or hash related to the user or service configuration.

Example: "qkhgerjqwhgrqjhwgrhqwjgrq"
Notes
Ensure that the data parameter is properly base64-encoded and contains valid JSON format.
Handle errors gracefully and provide meaningful error messages to assist in troubleshooting.
Example Workflow
Request: A user requests information by providing a base64-encoded data parameter.
Processing: The server decodes the data, retrieves the relevant VPN service details from Redis, and processes the information.
Response: The server responds with a JSON object containing the VPN service details or an error message.
For more information or support, please contact our technical support team.

