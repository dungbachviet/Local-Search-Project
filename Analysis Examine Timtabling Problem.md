
# LOCAL SEARCH PROJECT - EXAMINE TIMETABLING PROBLEM (BÀI TOÁN XẾP LỊCH THI)

## 1. Yêu cầu của Bài toán Xếp lịch thi

- Cho tập gồm n lớp học cần xếp lịch thi, tập m phòng học để tổ chức thi. Một ngày được chia thành 4 kíp (2 kíp sáng, 2 kip chiều)

- Thêm yếu tố : 
  - Số lượng giảng viên đăng ký trông thi (Họ sẽ đăng ký trông thi theo lịch rảnh của họ? Vậy nếu sau khi xếp lịch thi rồi mới cho họ đăng ký hay cho họ đăng ký trước rồi mới tiến hành xếp một thể? Yếu tố trông thi phụ thuộc vào lịch rảnh của họ? Trường hợp không may khi có một giảng viên bị ốm (bệnh tật), liệu có cách nào để phòng bị tình huống đó (để họ tự tìm người thay thế hay mình chủ động có phương án giảng viên dự bị)? Người trông thi nếu có việc bận họ sẽ báo trước 1-2 ngày để ban giám hiệu tìm người khác?). Một phòng thi sẽ cho phép bao nhiêu cán bộ trông thi (phòng như thế nào được 1 cán bộ, như thế nào được 2 cán bộ trông thi) ==> Nếu vậy cần có hàm mục tiêu về Giảm chi phí thuê người trông thi, và mục tiêu về Tối thiểu khả năng rủi ro xảy ra (ví dụ khi cán bộ trông thi ốm, hoặc cần có những phòng thi dự bị trong tình huống khẩn cấp như hỏa hoạn,...)
  
  - Lịch bận của mỗi phòng thi : Mỗi phòng thi sẽ có một tập danh sách các lịch bận (ngày-kíp thi) (Đây là lịch bận cho các hoạt động khác như tổ chức sự kiện, hội thảo,...)
  
  - Tập các ngày có thể tổ chức thi : Tức tránh những ngày lễ sinh viên được nghỉ - không phải thi. Sẽ không tổ chức thi vào những ngày này, nhưng liệu có tính ngày này vào thời gian sinh viên được nghỉ ôn tập (Nếu có tính thì "hơi bất công" cho sinh viên vì ngày lễ tết cũng phải ôn tập bài vở, nhưng nếu không tính thì ...? ==>Nên lựa chọn theo hướng nào ???)
  
  - Tập danh sách các lớp thi có chung sinh viên !!!
  
  - Cần có một danh sách về mức độ khó (tăng dần của các lớp thi) ==> Để cố gắng phân bổ những học phần dễ xen kẽ vào các học phần khó (tránh thi nhiều môn quá nặng liên tiếp ==> Nên sắp xếp xen kẽ hoặc như thế nào đó để sinh viên có thêm nhiều thời gian ôn tập)


  - Dữ liệu về Sức chứa của mỗi phòng thi (3 loại Lớn - Bình Thường - Nhỏ tương ứng với số ghế trong phòng)


- Cần sắp xếp lịch thi cho các lớp học (theo khuôn dạng Ngày thi - Kíp thi - Phòng thi), sao cho thỏa mãn (đáp ứng) các ràng buộc sau : 
  - Ràng buộc 1 - Sức chứa của mỗi phòng thi : Sức chứa của phòng thi phải có khả năng chứa đủ chỗ cho sinh viên của lớp thi được xếp vào tương ứng
  
  - Ràng buộc 2 - Tính công bằng cho các lớp thi cùng môn : Các lớp thi cùng Học phần sẽ thi cùng một thời điểm (tức cùng ngày, cùng kíp và khác lớp thi)
    - Vấn đề 1: Nếu số phòng được cung cấp không đáp ứng được đủ cho các lớp cùng môn thi cùng một thời điểm??? ==>Vậy thì yếu tố công bằng sẽ được thực hiện như thế nào? (Rõ ràng đối với sinh viên năm nhất, khi các môn đại cương sẽ được học chung rất nhiều, các thầy cô sẽ thường tạo ra các mã đề thi khác nhau) ==> Hãy suy nghĩ vấn đề này !!!

  - Ràng buộc 3 - Lịch bận của mỗi phòng thi : Không xếp lớp thi vào lịch bận của mỗi phòng thi
  
  - Ràng buộc 4 - Tính chiếm dụng duy nhất tại phòng thi: Tại mỗi thời điểm, phòng thi chỉ được tổ chức thi cho tối đa 1 lớp (nghĩa là : không thể 2 lớp cùng bị xếp vào 1 phòng thi và cùng kíp thi) ==> Nghĩa là 2 lớp được xếp vào cùng phòng thi phải được xếp vào khác thời gian (khác ngày hoặc nếu cùng ngày thì phải khác kíp thi)
  
  - Ràng buộc 5 - Lịch bận của các cán bộ trông thi : Lịch trông thi của cán bộ không bị trùng vào lịch bận của họ
  
  - Ràng buộc 6 - Tính không trùng : Tại một kíp thi, 1 cán bộ trông thi chỉ được xếp vào nhiều nhất 1 lớp (tránh tình trạng 1 cán bộ bị "phân thân" trông thi 2 lớp tại 1 thời điểm)
  
  - Ràng buộc 7 - Không tổ chức thi cùng kíp cho những lớp thi có chung sinh viên (Như vậy cần phải có 1 tập danh sách các lớp có chung sinh viên và không thể bị thi đồng thời)
  
  - Ràng buộc 8 - Nếu có 2 môn thi được tổ chức thi trong cùng 1 ngày thì cần phải cách nhau ít nhất 1 kíp thi
  - Ràng buộc 9 - Không cho phép giảng viên trông thi môn mà mình đang dạy 
  
- Mục tiêu hướng đến :
  
  - Mục tiêu 1 - Tối đa hóa Khoảng cách giữa các lần thi : Tránh tình trạng sinh viên phải liên tiếp quá nhiều môn thi ==> Cố gắng trải dài lịch thi cho sinh viên để : sinh viên có khoảng thời gian ôn tập đủ dài (mặc định sinh viên có 1 tuần dự trữ để ôn tập) + Khoảng cách giữa môn thi của 1 sinh viên phải cách nhau đủ xa (ví du : Chỉ cho phép tối 2 được thi 2 môn trong cùng 1 ngày, và nếu thi cùng ngày thi 2 môn đó phải thi cách nhau ít nhất 1 kíp. Nhưng hàm mục tiêu cần hạn chế khả năng thi cùng một ngày (tức hạn chế được thì càng tốt), mong muốn thì trong các ngày khác nhau thì càng tốt, đặc biệt khoảng cách giữa các ngày phải đủ lâu để trải dài trong toàn bộ thời gian thi)
  
  
  - Mục tiêu 3 - Tối đa hóa thời gian rảnh liền mạch cho cán bộ trông thi (Cố gắng để cán bộ trông thi trông liên tiếp trong ngày, tránh để họz phải trông trong nhiều ngày rời rạc)
  
  - Mục tiêu 4 - Tính phân bố đều đặn các lớp cho các phòng thi : Trong cùng một ngày thi, cố gắng phân bố các lớp thi đều đặn cho từng phòng thi ==> Tính đều đặn trên các khu vực (mỗi khu vực có thể có một số phòng thi)
  
  - Mục tiêu 5 - Tại một khu vực (có nhiều phòng thi), tránh hiện tượng ùn tắc, quá tải trong 1 kíp (tích hợp trọng số về tính ùn tắc của mỗi kíp thi)
    - ??? Vấn đề nhỏ : Liệu có dựa vào mục tiêu này có thể giúp giảm thiểu tình trạng đi quá nhiều vào các giờ cao điểm (những giờ cao điểm tập trung quá trình sinh viên đi thi tại một nơi, tránh tình trạng sinh viên đi đi quá nhiều trong 1 cùng kíp)
	==> Tức phải tạo thêm 1 mục tiêu nữa : Cân bằng số lượng sinh viên theo kíp thi hoặc nên ưu tiên vào những kíp thi nào đó ví dụ như cố gắng hạn chế sự tập trung các kíp thi vào kíp cuối vì sau đó là giờ cao điểm gây ùn tắc giao thông (Mục tiêu này khác với mục tiêu 4 là cân bằng vào các phòng thi xét trong 1 ngày)
  
  
  - Mục tiêu 6 : Các lớp thi thuộc cùng bộ môn nên được sắp trong một số tập các phòng thi gần như cố định (để sinh viên dễ nhớ) và gần nhau ??? (Hãy suy nghĩ về 2 yếu tố "gần cố định " và "gần nhau")
  
  - Mục tiêu 7 : Tạo điều kiện thuận lợi cho việc đi lại của các cán bộ trông thi giữa các phòng thi ???
  
  - Mục tiêu 8 : Dựa vào mức độ khó của các môn thi thuộc cùng Bộ môn, từ đó phân bổ xen kẽ "khó - dễ " !!!
  
  - Mục tiêu 9 : Hạn chế ít nhất số phòng cần sử dụng (tức ko được sử dụng các phòng một cách bừa bãi, nên phân bố hợp lý và tận dụng tối đa công suất của mỗi phòng)
 
  
## 2. Xây dựng mô hình bài toán 

- Biểu diễn các biến?
  - Biến giúp phân bố từng Lớp thi vào Ngày thi - Kíp thi - Phòng thi - Các cán bộ coi thi
  
  
- Biểu diễn các tập ràng buộc?
- Định nghĩa hàm mục tiêu?

