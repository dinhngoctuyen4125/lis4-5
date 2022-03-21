# Wooden Sticks
<ul>
  <li> Trc hết xem xét bài Chia dãy, một cách tóm tắt nhất, bài này hỏi: Số lis mà mảng A ban đầu tách ra được <b> ít nhất </b> là bao nhiêu? Vấn đề này sẽ giải quyết bằng cách tìm <i> dãy con giảm dài nhất </i> của mảng A ( do mỗi phần tử trong dãy giảm này ko thể ghép với phần tử nào có chỉ số thấp hơn cùng trong dãy này, để tạo thành 1 lis nào đó, như vậy mỗi phần tử trg <i> dãy con giảm dài nhất </i> phải nằm trong các lis khác nhau) </li>
  <li> Quay trở lại với bài này, bài hỏi tương tự với bài Chia dãy, nhưng các phần tử trong lis phải lớn hơn phần tử trc nó theo cả 2 chiều ( chiều <i> .first() </i> và chiều <i> .second() </i> Như vậy, ta chỉ cần sort chiều <i> .first() </i> cho dãy ban đầu, và tìm <i> dãy con giảm dài nhất </i> theo chiều <i> .second() </i> tương tự bài Chia dãy</li>
</ul>

