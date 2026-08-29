# Vode

**Vode** = **V**ibe c**ode**.

Vode là một skill giúp AI coding agent biến ý tưởng thành một sản phẩm có thể sử dụng và đưa cho người thật dùng, theo một quy trình đơn giản, thẳng vào vấn đề và bám sát điều bạn thực sự muốn.

[English](README.md)

## BUILD là phần lõi

Vode là phiên bản có thể thực thi của workflow BUILD:

**B**rainstorm -> **U**nderstand -> **I**mplement -> **L**aunch -> **D**istribute

5 verb này vẫn là các mốc chính của vòng đời sản phẩm. Vode bổ sung các verb như `decide`, `plan`, `debug`, `review`, `refine`, `iterate`, `pivot` và `resume` để bạn có thể bắt đầu đúng từ trạng thái hiện tại của project.

Bạn không cần chạy đủ mọi bước.

## Tại sao cần Vode?

Vibecoding rất nhanh khi AI hiểu đúng sản phẩm. Nó trở nên khó chịu khi AI:

- tự đoán quá nhiều
- code khi ý tưởng còn chưa rõ
- over-engineer
- thêm hạ tầng chưa cần thiết
- refactor những phần không liên quan
- phá các quyết định đã chốt trước đó

## Cài đặt

Với Skills CLI:

```bash
npx skills add namnth2000/vode -a codex -g
```

Chỉ cài cho project hiện tại:

```bash
npx skills add namnth2000/vode -a codex
```

Với coding agent khác, copy thư mục `skills/vode/` vào thư mục skills mà agent đó hỗ trợ. Phần lõi của Vode không phụ thuộc vào model hay tên tool cụ thể.

## Không cần nhớ câu lệnh

Bạn có thể gọi verb rõ ràng:

```
vode brainstorm
vode plan
vode implement
vode review
```

Nhưng cũng có thể nói tự nhiên:

```
vode gợi ý bước tiếp theo
vode làm gì tiếp?
vode tôi đang băn khoăn có nên thêm đăng nhập không
vode tôi đang nghĩ sửa chỗ này như vậy có tốt hơn không
vode chỗ này bị lỗi trên mobile
vode xem lại giúp tôi xem đã ổn chưa
```

Vode sẽ route theo ý định.

## Các verb

| Verb | Khi nào dùng | Mặc định có sửa code? |
| --- | --- | --- |
| `brainstorm` | Đang suy nghĩ, băn khoăn, muốn mở rộng hoặc thu hẹp ý tưởng | Không |
| `understand` | Muốn làm rõ sản phẩm, người dùng, core flow, scope | Không |
| `decide` | Cần chọn giữa một vài phương án cụ thể | Không |
| `plan` | Ý tưởng đã tương đối rõ và cần chia thành các bước build | Không |
| `implement` | Build một phần sản phẩm có thể dùng được | Có |
| `debug` | Có bug hoặc hành vi không đúng | Có |
| `review` | Muốn đánh giá lại product, UX, scope hoặc implementation | Không |
| `refine` | Sản phẩm đã chạy nhưng cần cải thiện, polish | Có |
| `launch` | Chuẩn bị public/release cho người dùng thật | Thường có |
| `distribute` | Tìm cách tiếp cận user và lấy feedback | Không |
| `iterate` | Có feedback/usage/new ideas và cần chọn phiên bản tiếp theo | Không |
| `pivot` | Sản phẩm không đi đúng hướng và cần cân nhắc đổi hướng | Không |
| `resume` | Muốn biết project đang ở đâu và nên làm gì tiếp | Không |
| `build` | Để Vode tự điều phối bước phù hợp từ trạng thái hiện tại | Tùy bước |

## Một vài ví dụ

### "Giờ làm gì tiếp?"

```
vode gợi ý bước tiếp theo
```

hoặc:

```
vode làm gì tiếp?
```

Vode sẽ route vào `resume`.

Nếu có thể, nó sẽ xem theo thứ tự hợp lý:

1. ngữ cảnh conversation hiện tại
2. hướng dẫn và docs của project
3. trạng thái source code hiện tại
4. diff hoặc thay đổi chưa hoàn tất
5. commit history gần đây nếu cần để hiểu vì sao project đang ở trạng thái này

Sau đó Vode trả lời:

- project đang ở đâu
- cái gì đã xong
- điều gì còn chưa rõ hoặc còn rủi ro
- bước tiếp theo có giá trị nhất
- vì sao nên làm bước đó trước

Nó không tự tạo feature mới chỉ vì backlog trống.

### "Tôi đang băn khoăn..."

```
vode tôi đang băn khoăn có nên dùng CodeMirror cho editor không
```

Vode route vào `brainstorm`.

Nó phân tích trước, không code ngay.

### Ý tưởng chưa rõ

```
vode build
Tôi muốn làm một app giúp chăm em bé.
```

Nếu những thông tin còn thiếu thực sự ảnh hưởng lớn đến sản phẩm, Vode sẽ hỏi một nhóm câu hỏi ngắn. Nếu có thể suy luận an toàn từ context hiện tại, nó sẽ không hỏi lại những gì đã biết.

### Có bug

```
vode nút Preview đang che heading trên màn hình 375px, sửa giúp tôi
```

Vode route vào `debug`:

**inspect -> tìm nguyên nhân thật -> sửa nhỏ nhất -> verify phần bị ảnh hưởng**

Không nhân tiện refactor cả project.

## Triết lý

Vode ưu tiên:

- sản phẩm hơn công nghệ
- chạy được hơn hoàn hảo trên lý thuyết
- làm rõ ý định hơn tự đoán
- stack đơn giản nhất đủ giải quyết bài toán hiện tại
- thay đổi nhỏ, coherent hơn rewrite lớn
- giữ các quyết định đã tồn tại hơn preference của AI
- usage thật hơn infrastructure cho tương lai chưa chắc xảy ra
- launch hơn polish vô hạn
- feedback hơn tích lũy feature

Vode không biến model yếu thành model mạnh. Mục tiêu của nó là giảm số quyết định quan trọng mà model phải tự đoán.

## Dành cho maintainer

Xem [TECHNICAL.md](TECHNICAL.md) để hiểu routing, cấu trúc thư mục, nguyên tắc maintain và cách thêm/sửa verb.

## License

MIT.
