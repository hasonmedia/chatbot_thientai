FROM python:3.11-slim

# Thiết lập thư mục làm việc
WORKDIR /app

# 1. Cài đặt các gói hệ thống cần thiết cho RUNTIME (Không cần build-essential)
RUN apt-get update && \
    apt-get install -y --no-install-recommends libpq5 \
    && rm -rf /var/lib/apt/lists/*

# 2. Copy các Python dependencies đã được cài đặt từ Stage Builder
COPY --from=builder /usr/local/lib/python3.11/site-packages /usr/local/lib/python3.11/site-packages

# 3. Copy toàn bộ mã nguồn ứng dụng
COPY . .

# 4. Expose port
EXPOSE 8000

# 5. Lệnh chạy ứng dụng bằng Uvicorn
# Lưu ý: Nếu có lỗi kết nối DB, bạn nên dùng ENTRYPOINT là một script chờ (entrypoint.sh)
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000", "--loop", "asyncio"]
