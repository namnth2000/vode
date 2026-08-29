# Semantic routing

Routing chooses the verb that best matches the user's dominant intent.

Exact phrases are examples, not a parser.

## Route table

### brainstorm

Use when the user is exploring open-ended possibilities or uncertainty.

Signals:

- "I'm thinking..."
- "I'm wondering..."
- "what if..."
- "any better idea?"
- "tôi đang băn khoăn..."
- "tôi đang nghĩ..."
- "liệu có nên..."
- "có hướng nào hay hơn không?"
- "sửa như này có tốt hơn không?"

If the user has two or three concrete options and wants a choice, use `decide` instead.

### understand

Use when the user wants to clarify what the product should be before planning/building.

Signals:

- unclear product idea
- unclear user/problem
- define MVP
- clarify requirements
- "giúp tôi làm rõ ý tưởng"
- "tôi muốn làm X nhưng chưa rõ nên gồm những gì"

### decide

Use when choosing between concrete alternatives.

Signals:

- A or B
- should I use X?
- keep or remove?
- now or later?
- "nên chọn cái nào"
- "có nên dùng..."
- "X hay Y"

### plan

Use when direction is sufficiently clear and the user needs an implementation path.

Signals:

- plan this
- break this into steps
- what order should I build?
- "lập kế hoạch"
- "chia thành các bước"
- "bắt đầu build từ đâu"

### implement

Use for requested feature creation or product changes that are not primarily bug fixes.

Signals:

- implement
- add
- create
- build this feature
- "làm giúp tôi"
- "thêm..."
- "tạo..."

If requirements are materially unclear, run the clarification protocol before editing.

### debug

Use when observed behavior is broken or incorrect.

Signals:

- error
- bug
- broken
- crash
- doesn't work
- overlap caused by regression
- "bị lỗi"
- "không chạy"
- "không hoạt động"
- "bị vỡ"

A request may include "fix it"; it still routes to `debug`.

### review

Use when the user asks for an assessment without requesting immediate edits.

Signals:

- review
- audit
- evaluate
- is this good?
- "đánh giá"
- "xem lại"
- "ổn chưa?"
- "có vấn đề gì không?"

### refine

Use when the product works but needs focused improvement.

Signals:

- polish
- improve
- simplify
- make this feel better
- "cải thiện"
- "polish"
- "làm cho tự nhiên hơn"
- "đỡ AI hơn"
- "gọn hơn"

If behavior is actually broken, route `debug`.

### launch

Use when preparing or performing release/publication.

Signals:

- launch
- deploy
- public
- release
- production
- domain
- "đưa lên mạng"
- "public"
- "release"

### distribute

Use for acquisition, communication, and feedback channels after or around launch.

Signals:

- get users
- promote
- launch post
- content
- communities
- marketing
- "tìm user"
- "quảng bá"
- "phân phối"
- "đăng ở đâu"

### iterate

Use when turning real feedback, usage, analytics, bugs, or accumulated ideas into the next version.

Signals:

- feedback
- analytics
- v2
- next version based on usage
- "feedback này nên xử lý thế nào"
- "phiên bản tiếp theo"
- "nên ưu tiên cái gì tiếp"

### pivot

Use when questioning the product direction itself.

Signals:

- nobody uses this
- wrong audience
- should I abandon it?
- change direction
- "không ai dùng"
- "có nên bỏ không"
- "đổi hướng"
- "pivot"

### resume

Use when the user wants Vode to understand current project state and recommend the next step.

Signals:

- "vode what next?"
- "what should I do next?"
- "continue this project"
- "where are we?"
- "vode gợi ý bước tiếp theo"
- "vode làm gì tiếp?"
- "tiếp theo nên làm gì?"
- "giờ làm gì?"
- "tiếp tục project này"

### build

Use when the user asks Vode to take a product forward broadly without naming a stage.

Signals:

- "vode build"
- "build this idea with Vode"
- "take this from idea to something usable"
- "vode làm sản phẩm này giúp tôi"

## Tie-breakers

- explicit verb wins
- broken behavior -> debug
- finite options -> decide
- open-ended uncertainty -> brainstorm
- assessment without edits -> review
- working-but-needs-better -> refine
- "what next?" in an existing project -> resume
- broad forward motion -> build

If two routes remain equally plausible and the difference would change whether files are edited, prefer the non-editing route or ask one short clarification.
