# E字视力测试

Web版视力测试应用，基于标准E字视力表（Tumbling E Chart）。

## 在线访问

**生产环境**: https://eye.zhangtianle.cn

## 功能特性

- 三端适配：PC（信用卡校准）、Pad（银行卡校准）、手机（硬币校准）
- 屏幕校准：手动滑块对齐，确保E字尺寸精确
- 视力预选：滑动选择大概范围，实时预览E字大小
- 阶梯测试：每级3题，≥2正确通过
- 即时反馈：正确绿色/错误红色+震动
- 双眼分别测试，显示5分记录+小数记录

## 本地开发

```bash
# 直接用浏览器打开
open index.html
# 或启动简单服务器
python3 -m http.server 8080
```

## 部署检查清单

每次代码迭代后，部署前检查：

### 1. 代码检查
- [ ] HTML语法正确
- [ ] JS无明显语法错误
- [ ] 测试逻辑正确（阶梯法）

### 2. 本地测试
- [ ] 页面正常加载
- [ ] 校准滑块正常工作
- [ ] 视力预选滑块实时预览
- [ ] 方向按钮响应正确
- [ ] 键盘方向键正常工作
- [ ] 结果页显示正确

### 3. 部署步骤
```bash
# 1. 复制文件到网站目录
sudo cp index.html /var/www/eye/html/

# 2. 验证文件权限
ls -la /var/www/eye/html/

# 3. 测试本地访问
curl -H "Host: eye.zhangtianle.cn" http://127.0.0.1/

# 4. 验证在线访问
curl -I https://eye.zhangtianle.cn
```

### 4. 生产验证
- [ ] 域名可访问
- [ ] 页面正常加载
- [ ] 校准功能正常
- [ ] 测试流程完整

## 部署信息

| 项目 | 值 |
|------|-----|
| 域名 | eye.zhangtianle.cn |
| Web目录 | /var/www/eye/html |
| Nginx配置 | /etc/nginx/sites-available/eye.conf |
| 默认距离 | PC:5m, Pad:3m, 手机:2.5m |

## 技术栈

- 纯HTML + CSS + JavaScript
- Canvas绘制E字
- 无外部依赖