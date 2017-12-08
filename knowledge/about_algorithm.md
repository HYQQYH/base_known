### about algorithm

 1. 使用fst解析正则表达式:
 >`例子:<company>(公司)?(的)?(cto|首席技术官) => (cto,[])`
 >逐字匹配
 >a.双指针:cursor_head, cursor_tail = 0, 1
 >b.使用`segment_stack = [{'start_of_this_segment':0, 'end_of_this_segment':0, 'value':'<eps>','head_arc'=[cursor_head, cursor_tail]}]`
 >\#该栈用于更新`()`的起始位置,当遇到`(`时,更新`start_of_this_segment`,遇到`)`时,更新`end_of_this_segment`
 >c.如果当前`word=='('`,更新`'start_of_this_segment':cursor_tail`,同时更新`'head_arc'=[cursor_head, cursor_tail]`用于记录上一个字的结尾与当前`(`开始的索引.
 >d.如果当前`word==')'`,更新`'end_of_this_segment':cursor_head`,若当前词为`)?`,则取出`'start_of_this_segment'和'end_of_this_segment'`,进行链接.
 >e.处理`(|)`的情况,需记录`(`的位置`'start_of_this_segment':cursor_tail`,当前word为`|`时,更新cursor_head为`cursor_head = segment_stack[-1]['start_of_this_segment']`,同时,记录当前位置:`'end_of_this_segment':cursor_head`,当前word为`)`或`)?`时,取出`cursor_head = segment_stack[-1]['end_of_this_segment']`