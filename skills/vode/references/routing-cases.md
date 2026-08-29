# Routing regression cases

Use these cases when changing Vode routing.

| Input | Expected verb | Why |
| --- | --- | --- |
| `vode what next?` | resume | asks for next step from current state |
| `vode gợi ý bước tiếp theo` | resume | Vietnamese next-step request |
| `vode làm gì tiếp?` | resume | Vietnamese next-step request |
| `vode tiếp tục project này` | resume | continuation |
| `vode tôi đang băn khoăn có nên thêm login không` | brainstorm | open uncertainty |
| `vode tôi đang nghĩ sửa chỗ này như vậy có tốt hơn không` | brainstorm | explores an improvement |
| `vote tôi đang băn khoăn có nên thêm login không` in an established Vode conversation | brainstorm | obvious Vode typo in context |
| `vote cho ứng viên nào?` | none | ordinary voting language, not Vode |
| `vode localStorage hay D1?` | decide | concrete alternatives |
| `vode có nên thêm CodeMirror bây giờ không?` | decide | yes/no product choice |
| `vode giúp tôi làm rõ MVP app chăm bé` | understand | clarify product definition |
| `vode chia feature này thành các bước implement` | plan | implementation sequence |
| `vode thêm export PDF` | implement | direct feature request |
| `vode export PDF đang crash` | debug | broken behavior |
| `vode export PDF đang crash, sửa giúp tôi` | debug | fix request still begins with bug diagnosis |
| `vode review UI hiện tại` | review | assessment only |
| `vode làm UI này đỡ AI hơn` | refine | working UI, focused improvement |
| `vode chuẩn bị public app này` | launch | release readiness |
| `vode tôi nên đăng app này ở đâu để có user đầu tiên?` | distribute | acquisition |
| `vode đây là feedback tuần đầu, nên làm V2 thế nào?` | iterate | feedback -> next version |
| `vode không ai dùng, có nên đổi hướng không?` | pivot | product direction |
| `vode build app Markdown to PDF này` | build | broad orchestration |

## Regression rule

When a routing change fixes one phrase but breaks a neighboring intent, prefer improving the semantic rule instead of adding more literal phrase matching.
