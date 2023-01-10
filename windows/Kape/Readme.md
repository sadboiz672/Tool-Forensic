#1. KAPE là gì?

Kroll Artifact Parser and Extractor (KAPE) là một chương trình phân loại, phân tích mục tiêu từ một thiết bị hoặc vị trí lưu trữ, tìm các thông tin có liên quan. 
KAPE cho phép các nhà điều tra tìm và ưu tiên các hệ thống quan trọng hơn đối với trường hợp của họ. Ngoài ra, KAPE có thể được sử dụng để thu thập các thông tin quan trọng trước khi bắt đầu quá trình phân tích. 

#2. Cách thức hoạt động của KAPE

KAPE phục vụ hai chức năng chính: 
1) Thu thập tệp
2) Xử lý tệp đã thu thập bằng một hoặc nhiều chương trình. 

Bản thân KAPE không làm bất cứ điều gì liên quan đến một trong hai chức năng này; đúng hơn, chúng đạt được bằng cách đọc nhanh các tệp cấu hình và dựa trên nội dung của các tệp này, thu thập và xử lý tệp. Điều này làm cho KAPE rất dễ mở rộng trong việc thêm hoặc mở rộng chức năng.

KAPE sử dụng các khái niệm về mục tiêu và mô-đun để thực hiện công việc của mình. KAPE đi kèm với một loạt các mục tiêu và mô-đun mặc định cho hầu hết các hoạt động phổ biến cần thiết trong hầu hết các kỳ thi pháp y. Chúng cũng có thể được sử dụng làm ví dụ để làm theo để tạo các mục tiêu và mô-đun mới.

Ở cấp độ cao, KAPE hoạt động bằng cách thêm mặt nạ tệp vào hàng đợi. Hàng đợi này sau đó được sử dụng để tìm và sao chép các tệp từ một vị trí nguồn. Đối với các tệp bị khóa bởi hệ điều hành, quá trình thứ hai sẽ diễn ra để bỏ qua việc khóa. Khi kết thúc quá trình, KAPE sẽ tạo một bản sao và lưu giữ siêu dữ liệu về tất cả các tệp có sẵn từ một vị trí nguồn vào một thư mục nhất định.

Giai đoạn xử lý thứ hai (tùy chọn) là chạy một hoặc nhiều chương trình đối với dữ liệu đã thu thập. Điều này hoạt động bằng cách nhắm mục tiêu tên tệp hoặc thư mục cụ thể. Các chương trình khác nhau được chạy đối với các tệp và đầu ra từ các chương trình sau đó được lưu trong các thư mục được đặt tên theo một danh mục, chẳng hạn như EvidenceOfExecution, BrowserHistory, AccountUsage, v.v.

Bằng cách nhóm mọi thứ theo danh mục, người kiểm tra ở mọi cấp độ có phương tiện để khám phá thông tin liên quan bất kể hiện vật riêng lẻ mà một phần thông tin đến từ đâu. Nói cách khác, người kiểm tra không còn cần phải biết xử lý tìm nạp trước, shimcache, amcache, userassist, v.v. vì nó liên quan đến bằng chứng về tạo tác thực thi. Bằng cách suy nghĩ phân loại và nhóm đầu ra theo cùng một cách, có thể tận dụng phạm vi tạo phẩm rộng hơn cho bất kỳ yêu cầu nhất định nào.


Tiếp tục...
Tất nhiên, có nhiều chi tiết hơn trong sách hướng dẫn (rất hay, hãy đọc nó!), nhưng hãy xem xét một số tình huống sử dụng và cách làm cho nó thực hiện điều gì đó tiếp theo.

KAPE có thể được sử dụng trên hệ thống đang hoạt động hoặc chống lại hệ thống hộp chết ở dạng ổ cứng bị chặn ghi hoặc E01 được gắn. Trong mọi trường hợp, cách sử dụng là như nhau. KAPE cũng xử lý các tệp đang sử dụng và các bản sao khối lượng tối, làm cho nó trở nên rất kỹ lưỡng trong cách tiếp cận tìm kiếm và thu thập dữ liệu.

Điều đáng nói ở đây là KAPE muốn ký tự ổ đĩa, thư mục hoặc đường dẫn UNC làm nguồn dữ liệu của nó. Nếu bạn có thể trỏ KAPE vào một đường dẫn, nó sẽ thực hiện công việc của nó.

Vì vậy, trong trường hợp hệ thống đang hoạt động, chúng tôi chỉ cần cung cấp KAPE bằng cách kết nối một số loại bộ nhớ ngoài chẳng hạn. Từ đó, chúng tôi có thể nhắm mục tiêu bất kỳ ký tự ổ đĩa hoặc thư mục nào để thu thập.

Đối với hệ thống hộp chết, sau khi Windows nhận ra thiết bị bị chặn ghi hoặc bạn đã gắn E01 (sử dụng Arsenal Image Mounter, KHÔNG FTK Imager ) và nó đã được gán một ký tự ổ đĩa, bạn đã sẵn sàng để bắt đầu.

Tại thời điểm này, chúng tôi giả định rằng bạn có sẵn một ký tự ổ đĩa đích. Một số ví dụ sẽ được hiển thị tại một số điểm bên dưới, cho cả hệ thống trực tiếp cũng như hình ảnh được gắn (một lần nữa, hãy sử dụng Arsenal Image Mounter. FTK Imager không hiển thị các bản sao bóng ổ đĩa).


mục tiêu
Các mục tiêu chịu trách nhiệm xác định các tệp và thư mục để KAPE sao chép. Thông số kỹ thuật đầy đủ cho một mục tiêu và các thuộc tính của nó có trong sách hướng dẫn, nhưng nó khá đơn giản.

Các mục tiêu (và mô-đun) được viết bằng YAML. Đây là một định dạng dễ sử dụng và dễ hiểu và nhiều ví dụ được đưa vào KAPE.

Mục tiêu cho các tạo phẩm hệ thống tệp trông giống như sau:



Đây là một ví dụ đơn giản trong đó chúng tôi vừa chỉ định đường dẫn đầy đủ cho từng tệp mà chúng tôi quan tâm. Trong một số trường hợp, như $MFT và $SDS, chúng tôi phải sử dụng một thuộc tính bổ sung, AlwaysAddToQueue, bởi vì Windows sẽ, trên một tệp đang chạy. hệ thống, nói dối và nói rằng tệp đó không tồn tại (dù sao cũng thông qua các phương tiện thông thường).

Hãy xem xét một ví dụ khác:




Một lần nữa, chúng ta thấy các đường dẫn được chỉ định cho các tạo phẩm, nhưng điều khác biệt ở đây là việc sử dụng các ký tự đại diện. Chúng tôi không có cách nào để biết trước tất cả các cấu hình trên máy tính, vì vậy ký tự đại diện được KAPE tự động mở rộng để tìm tất cả các cấu hình tồn tại, sau đó lấy tất cả các tệp lnk tồn tại (sử dụng lại ký tự đại diện, vì chúng tôi không có ý tưởng tên sẽ là gì).

Một thuộc tính thú vị khác là IsDirectory cùng với Đệ quy. Những thứ này cho phép bạn cung cấp một thư mục cơ sở và sao chép tất cả các tệp/thư mục bên dưới nó, chẳng hạn như danh sách nhảy trong ví dụ đầu tiên.


Với các mục tiêu được xác định (và KAPE đi kèm với gần hai chục mục tiêu trong số đó, từ hệ thống tệp đến Sổ đăng ký đến Nhật ký sự kiện đến Thùng rác, Outlook, v.v.), mục tiêu bạn quan tâm sẽ được chuyển vào KAPE và KAPE sẽ xử lý những việc sau :

Mở rộng tệp mục tiêu cho tất cả các tệp phù hợp
Cố gắng sao chép tệp bằng "thông thường" có nghĩa là
Nếu một tệp đang được sử dụng, hãy trì hoãn việc sao chép
Khi kết thúc quá trình sao chép thông thường, hãy xử lý tất cả các tệp bị hoãn lại bằng cách đọc đĩa thô để nhận bản sao của tệp
Tạo lại bất kỳ cấu trúc thư mục nào và áp dụng dấu thời gian có độ phân giải đầy đủ từ thư mục gốc
Sao chép tệp vào thư mục đích đích và áp dụng lại dấu thời gian có độ phân giải đầy đủ từ tệp nguồn
SHA-1 băm tệp
Ghi lại tất cả những điều này trong các tệp nhật ký
Tất cả điều này xảy ra trong vài giây tùy thuộc vào những gì bạn đang nhắm mục tiêu.

Mục tiêu bên trong mục tiêu bên trong mục tiêu (khởi đầu!)
Các mục tiêu cũng có thể tham chiếu các mục tiêu khác, nhưng điều này có nghĩa là gì? 

Trước khi đi sâu vào vấn đề đó, hãy nói về cách bạn nên thiết kế các mục tiêu và cách chúng được thiết kế cho đến nay.

Các mục tiêu phải cụ thể ở chỗ chúng tập trung vào một loại tệp hoặc nhiều tệp nhất định. Ví dụ: một mục tiêu phải chi tiết ở chỗ nó chỉ tìm nhật ký sự kiện. Một mục tiêu khác chỉ tìm tổ ong Registry. Tuy nhiên, một cái khác chỉ tìm các cấu hình Chrome, v.v.

Tại sao làm theo cách này? Bằng cách giữ mọi thứ chi tiết và cụ thể, BẠN có thể chọn chỉ nhắm mục tiêu những gì BẠN muốn. Nếu bạn chỉ muốn thông tin về Chrome và Firefox, bạn có thể chạy các mục tiêu đó. 

Nhưng còn trường hợp bạn không biết trình duyệt nào đang được sử dụng hoặc bạn muốn nhắm mục tiêu vào hệ thống tệp, tổ ong Registry và danh sách nhảy thì sao? 

Đây là lúc khái niệm về mục tiêu tổng hợp phát huy tác dụng. Hãy xem xét một:




Chuyện gì đang xảy ra ở đây vậy? Lưu ý rằng, thay vì đường dẫn tệp, ký tự đại diện, v.v., chúng tôi đang tham chiếu đến các tệp mục tiêu khác!

Khi KAPE chạy, nó sẽ tự động mở rộng từng mục tiêu ở trên bằng cách sử dụng những gì có trong tệp mục tiêu đó. Trong trường hợp này, các chi tiết từ InternetExplorer.tkape, Chrome.tkape và Firefox.tkape sẽ được mở rộng và từng tệp được định vị và sao chép! Nếu trình duyệt cụ thể đó không được cài đặt, dữ liệu đó sẽ không được tìm thấy.

Với suy nghĩ này, bạn có thể thấy cách tiếp cận này mạnh mẽ và linh hoạt như thế nào khi BẠN quyết định thu thập những gì và khi nào thu thập. Nếu bạn chỉ muốn các bản ghi sự kiện và tổ ong trong Sổ đăng ký, hãy sử dụng hai mục tiêu đó trong một mục tiêu mới có tên là HivesAndEventLogs.tkape, sau đó sử dụng mục tiêu đó.

Ngoài ra còn có một mục tiêu đặc biệt, !All, chỉ đơn giản là định vị tất cả các mục tiêu khác và chạy tất cả chúng. Mặc dù điều này hoạt động, nhưng nó sẽ không nhanh bằng việc sử dụng một nhóm mục tiêu cụ thể hơn cho bộ sưu tập.

mô-đun
Nói một cách đơn giản, các mô-đun chạy các chương trình. Cụ thể hơn, họ chạy một chương trình DUY NHẤT. Điều này rất quan trọng để hiểu vì các mô-đun được viết cho một mục đích duy nhất.

Hãy xem một ví dụ. Trong trường hợp này, một mô-đun cho PECmd được hiển thị bên dưới:



Như với các mục tiêu, thông số kỹ thuật đầy đủ cho một mô-đun được nêu trong sách hướng dẫn, nhưng nó khá đơn giản.

Nhóm Bộ xử lý chứa một hoặc nhiều mục nhập cho PECmd. Trong trường hợp này, có ba, vì PECmd biết cách xuất dữ liệu ở ba định dạng khác nhau. Nhìn vào tiêu đề, bạn có thể thấy ExportFormat được đặt thành 'csv', nghĩa là bộ xử lý đầu tiên trong danh sách sẽ được sử dụng (bộ xử lý có --csv switch).

Tên biến
Các giá trị được bao quanh bởi % là các biến mà KAPE sẽ thay thế khi chạy. Tất cả các biến có sẵn đều được chỉ định trong sách hướng dẫn cũng như trong tất cả các mô-đun đi kèm để tham khảo và lấy ví dụ, nhưng nó khá đơn giản. 

%sourceDirectory% sẽ được thay thế bằng giá trị của --msource.
%destinationDirectory% sẽ được thay thế bằng --mdest cộng với danh mục từ mô-đun (ProgramExecution trong trường hợp của PECmd)
Điều này cho phép KAPE hoạt động bất kể thư mục nguồn hay đích, ký tự ổ đĩa, đường dẫn UNC, v.v.

Xử lý chuyển hướng
Đây là một ví dụ khác về một mô-đun. Nó hơi giống nhau, nhưng lưu ý rằng có một thuộc tính bổ sung trong bộ xử lý, ExportFile .



Dòng lệnh ở đây khá cụ thể để chỉ xử lý một tệp. Vấn đề ở đây không phải là dòng lệnh, mà là sự hiện diện của ExportFile.

ExportFile được sử dụng khi một chương trình không biết cách lưu trực tiếp đầu ra của nó vào một tệp và dựa vào chuyển hướng dòng lệnh (ví dụ: qua >) để lưu kết quả. Vì giới hạn này với chương trình, bạn phải sử dụng thuộc tính ExportFile chỉ định nơi lưu kết quả đầu ra từ chương trình.

LƯU Ý: BẠN KHÔNG THỂ SỬ DỤNG CHUYỂN HƯỚNG trên Dòng lệnh! Đừng cố làm điều gì đó như thế này trong thuộc tính CommandLine:

D:\temp\HP._lnk > hpout.txt

vì nó SẼ KHÔNG HOẠT ĐỘNG.

Điểm đáng chú ý ở đây là bạn được đề cập trong cả hai tình huống mà chương trình có thể ghi trực tiếp vào một tệp, giống như PECmd, hoặc đối với các chương trình sử dụng chuyển hướng, bạn chỉ cần sử dụng ExportFile để ghi lại đầu ra. Bạn có thể đặt tên giá trị cho thuộc tính ExportFile bất kỳ tên tệp nào bạn muốn.


chạy KAPE
KAPE yêu cầu quyền của quản trị viên, vì vậy điều đầu tiên cần làm là mở dấu nhắc lệnh cấp quản trị hoặc cửa sổ PowerShell. Từ đó, việc chạy KAPE tự hiển thị cho chúng tôi tất cả các tùy chọn khả dụng.

Trước khi chúng tôi thấy nó được sử dụng, hãy dành một chút thời gian để xem xét các tùy chọn:




Mặc dù có khá nhiều tùy chọn, nhưng mọi thứ thường được chia thành hai loại chính: Mục tiêu và Mô-đun .

Tùy chọn mục tiêu bắt đầu bằng 't' và tùy chọn mô-đun bắt đầu bằng 'm' và được nhóm lại với nhau như minh họa ở trên.

Đối với các mục tiêu, --tsource,-- tdest và --target đều bắt buộc.

Đối với các mô-đun, --msource, --mdest và --module là bắt buộc. Tuy nhiên, có một ngoại lệ đối với quy tắc này mà chúng ta sẽ thấy sau. Khi sử dụng các tùy chọn mục tiêu và mô-đun cùng nhau, bạn có thể bỏ qua --msource và KAPE sẽ tự động gán giá trị cho --tdest cho --msource.

Xem các mục tiêu và mô-đun có sẵn
Lưu ý rằng có hai bộ công tắc liệt kê các mục tiêu và mô-đun:

--tlist và --tdetail
--mlist và --mdetail

Các lệnh 'danh sách' sẽ loại bỏ tên mục tiêu và thông tin khác về từng mục tiêu hoặc mô-đun. Ở đây chúng ta thấy --tlist đang hoạt động:



Nếu chúng ta thêm --tdetail vào lệnh, chúng ta sẽ nhận được điều này:



Lưu ý rằng tất cả thông tin đường dẫn bên trong mỗi mục tiêu cũng được hiển thị khi sử dụng --tdetail.

--mlist và --mdetail hoạt động theo cùng một cách, ngoại trừ chúng hiển thị các mô-đun có sẵn và thông tin chi tiết của chúng.
Tùy chọn nguồn mục tiêu
Công tắc --tsource cho KAPE biết nơi bắt đầu tìm kiếm tệp. Đây có thể là ổ đĩa cứng, ổ đĩa ngoài, mạng chia sẻ, ổ đĩa từ xa được ánh xạ F-Response, đường dẫn UNC, E01 được gắn, v.v. Miễn là nó có thể được tham chiếu bằng ký hiệu đường dẫn được Windows hỗ trợ, nó sẽ hoạt động.

Tùy chọn điểm đến mục tiêu
Công tắc --tdest cho KAPE biết nơi tạo bản sao của các thư mục và tệp mà nó định vị. Đây là trường hợp sử dụng đơn giản nhất.

Tuy nhiên, KAPE cũng có thể đặt các bản sao của các tệp mà nó tìm thấy bên trong bộ chứa VHD hoặc VHDX (ưu tiên) bằng cách sử dụng khóa chuyển --vhd hoặc --vhdx. Trong cả hai trường hợp, bạn cũng phải cung cấp tên cơ sở cho vùng chứa. Tên cơ sở này sẽ được sử dụng để đặt tên cho vùng chứa mà KAPE tạo. Nói cách khác, đây KHÔNG phải là tên đầy đủ của vùng chứa được tạo, mà chỉ là một phần của vùng chứa đó. 

Sử dụng tùy chọn này sẽ trông như thế này:

kape.exe --tsource c --tdest c:\temp\tout -- target bằng chứng thực thi --vhdx MyBaseNameExample

Điều này sẽ dẫn đến việc tất cả các tệp được tìm thấy sẽ được sao chép vào bộ chứa VHDX (nằm trong C:\temp\tout, có tên:

2019-02-13T172926_evidenceofexecution_MyBaseNameExample.vhdx

Có một số điều cần chú ý ở đây. Một là dấu thời gian ở phía trước. Thứ hai là tên của mục tiêu được bao gồm trong tên tệp (bằng chứng thực thi). Cuối cùng, chúng ta thấy tên cơ sở trước phần mở rộng.

Bởi vì chúng tôi đã sử dụng bộ chứa VHDX, điều này cho phép chúng tôi chỉ cần nhấp đúp vào bộ chứa để gắn nó vào Windows. Làm điều này dẫn đến một ký tự ổ đĩa mới hiển thị, như thế này:



(Để làm cho mọi thứ dễ nhìn hơn một chút, tôi chỉ hiển thị một số tệp Tìm nạp trước tồn tại trong VHDX để minh họa bố cục. Có hàng chục tệp tìm nạp trước khác trong VHDX thực tế.)

Hình ảnh trên là từ Directory Opus (trình quản lý tệp tốt nhất cho Windows hiện có!). Tuy nhiên, những gì hình ảnh hiển thị là các thư mục và tệp tồn tại trong VHDX ở định dạng được nhóm, dễ dàng xem những gì đang diễn ra hơn là sử dụng File Explorer.

Trước tiên, hãy chú ý nhãn ổ đĩa hiển thị ngày sản xuất hộp chứa. Nhìn sang phải, chúng ta thấy danh sách các tệp và thư mục trong bộ chứa VHDX. Đường dẫn đầy đủ đã được tạo lại từ C trở xuống vì chúng tôi đã yêu cầu KAPE xử lý ổ C thông qua --tsource.

Ngoài bản thân các tệp, hãy lưu ý rằng còn có hai tệp CopyLog, một tệp văn bản và một tệp CSV. Chúng chứa đầy đủ chi tiết về những gì KAPE đã làm:







Lưu ý rằng cả hai đều bao gồm đường dẫn nguồn, đường dẫn đích, SHA-1 nguồn và dấu thời gian từ tệp nguồn. CSV cũng thêm các chi tiết liên quan đến thời gian sao chép tệp và liệu tệp có bị khóa hay không (cột DeferredCopy).

Bản thân tất cả các tệp, như đã đề cập trước đây, đều có dấu thời gian đầy đủ được áp dụng cho chúng. Nhìn vào tệp tìm nạp trước bên trong vùng chứa, các thuộc tính trông giống như sau:




Lưu ý rằng dấu thời gian là từ tháng 12 chứ không phải ngày 13 tháng 2, tức là khi vùng chứa được tạo.

Tùy chọn VHD hoạt động chính xác theo cùng một cách, ngoại trừ bạn kết thúc bằng một bộ chứa VHD.

Lưu ý : lần đầu tiên bạn gắn một vùng chứa trong Windows, nó phải được thực hiện ở chế độ đọc-ghi! Sau khi nó được gắn và ngắt kết nối ban đầu, bạn có thể sử dụng PowerShell để gắn bộ chứa ở dạng chỉ đọc, nhưng PHẢI thực hiện rw lần đầu tiên nếu không Windows sẽ không nhận ra hệ thống tệp. Điều này không ảnh hưởng gì đến dữ liệu bên trong vùng chứa, chỉ chính tệp VHDX.


Để ngắt kết nối vùng chứa, nhấp chuột phải vào ký tự ổ đĩa mới và chọn Eject .




Trong các hình ảnh trên, lưu ý rằng thư mục trong thư mục gốc của vùng chứa là ổ C. Nếu chúng tôi sử dụng tùy chọn để xử lý các bản sao bóng của ổ đĩa, chúng tôi sẽ kết thúc với một bộ thư mục khác. Nếu chúng tôi đã chạy lệnh này (cùng một lệnh như trước, chúng tôi chỉ thêm --vss vào cuối):

kape.exe --tsource c --tdest c:\temp\tout -- target bằng chứng thực thi --vhdx MyBaseNameExample --vss

Chúng tôi sẽ thấy những điều sau đây khi chúng tôi gắn VHDX:




Lưu ý rằng chúng tôi có ba thư mục cấp cao nhất bổ sung, một thư mục dành cho mỗi VSC mà KAPE đã xử lý và tìm thấy các tệp phù hợp. Khi KAPE chạy, nó trông như thế này:





Ở đây chúng ta có thể thấy một số điều gọn gàng. Một là KAPE đó, chỉ bằng cách thêm công tắc --vss, định vị và gắn tất cả các bản sao ẩn trên ổ C. Sau đó, nó đi qua ổ C và từng VSC, định vị các tệp trên đường đi. Nó đã tìm thấy tổng cộng 1.039 tệp, nhưng chỉ sao chép được 829 tệp do các giá trị băm SHA-1 trùng lặp.  TOÀN BỘ VẬN HÀNH NÀY MẤT 7,4243 GIÂY.

Từ đây, chúng ta có thể thấy tệp VHDX được tạo và sau đó được nén (điều này làm cho tệp nhỏ hơn đáng kể để vận chuyển).

Tất cả đã nói, KAPE đã tìm thấy, sao chép và sao chép 829 tệp một cách hợp pháp, đặt chúng vào một thùng chứa VHDX, sau đó nén nó trong 10,7241 giây.

Một điều khác cần lưu ý trong đầu ra ở trên là có một số tệp đã bị khóa. Tuy nhiên, đây không phải là vấn đề vì bạn có thể thấy các tệp bị trì hoãn đã được sao chép ở cuối mà không có bất kỳ lỗi nào.

Bạn có thể sử dụng khóa chuyển --zv để tắt tính năng nén vùng chứa bằng cách thêm --zv false vào dòng lệnh.

Cuối cùng, các tệp VHD(x) do KAPE tạo ra có thể được đưa vào các công cụ như X-Ways Forensics để phân tích mục tiêu ngay lập tức!



Các tùy chọn mục tiêu khác
Tùy chọn --tflush yêu cầu KAPE xóa thư mục (nếu nó tồn tại) được chỉ định bởi --tdest trước khi ghi bất kỳ thứ gì vào đó. Điều này đảm bảo rằng KHÔNG có tệp hoặc thư mục nào khác trong --tdest trước khi KAPE đặt tệp ở đó (luôn luôn là một điều tốt).

Tùy chọn nguồn mô-đun
Công tắc --msource cho KAPE biết nơi bắt đầu tìm tệp để xử lý. Đây có thể là ổ đĩa cứng, ổ đĩa ngoài, mạng chia sẻ, ổ đĩa từ xa được ánh xạ F-Response, đường dẫn UNC, E01 được gắn, v.v., giống như chúng ta đã thấy với --tsource.

Đây không nhất thiết phải là thư mục đến từ tùy chọn đích, nghĩa là bạn có thể sử dụng KAPE để chạy phản hồi trực tiếp trên hệ thống đang chạy hoặc chống lại E01 được gắn mà không cần sử dụng tùy chọn Mục tiêu nếu muốn.

Tùy chọn đích mô-đun
Công tắc --mdest cho KAPE biết nơi hướng dẫn bộ xử lý lưu tệp vào. Nhớ lại rằng các mô-đun chạy một chương trình đối với các tệp. Đầu ra kết quả (ví dụ: tệp csv, json hoặc html) sẽ được lưu vào thư mục bên dưới thư mục được chỉ định bởi --mdest.

Tùy chọn mô-đun khác
Tùy chọn --mflush yêu cầu KAPE xóa thư mục (nếu nó tồn tại) được chỉ định bởi --mdest trước khi ghi bất kỳ thứ gì vào đó. Điều này đảm bảo rằng KHÔNG có tệp hoặc thư mục nào khác trong --mdest trước khi các mô-đun đặt tệp ở đó.

Công tắc --mef cho phép bạn ghi đè bộ xử lý mặc định như được chỉ định trong cấu hình mô-đun. Ví dụ: nếu bạn muốn đầu ra json từ mô-đun PECmd, bạn có thể sử dụng --mef json và KAPE sẽ chọn bộ xử lý thích hợp từ các bộ xử lý có sẵn được xác định trong mô-đun.

Hãy xem xét lệnh sau:

kape.exe --tsource c --tdest c:\temp\tout -- targetbằng chứng thực thi --tflush --mdest C:\Temp\mout --module PECmd --mflush

Điều này sẽ giống như:



Điều này tương tự như những gì chúng ta đã thấy với các mô-đun đích, nhưng hãy chú ý sau khi bản sao hoàn tất. KAPE bắt đầu xử lý dữ liệu với mô-đun PECmd. Điều này sẽ dẫn đến dữ liệu sau được tạo trong --mdest:



Vì Tìm nạp trước có liên quan đến bằng chứng thực thi, nên mô-đun PECmd có danh mục Thực thi chương trình được chỉ định trong tệp mô-đun. Nếu chúng tôi cũng chạy các mô-đun khác để xem xét bằng chứng về các tạo phẩm thực thi, như ammcompatcache hoặc amcache, thì các kết quả đó sẽ nằm trong cùng thư mục này vì các mô-đun đó cũng sử dụng cùng danh mục này.

Hai tệp CSV hiển thị ở trên có thể được mở và phân tích trong Timeline Explorer hoặc bất kỳ chương trình nào khác mà bạn chọn.

Lưu ý, trong trường hợp này, phải mất tới 2,6467 giây để tìm, sao chép và xử lý tất cả các tệp tìm nạp trước và sẵn sàng phân tích chúng.

Nếu chúng ta thêm tùy chọn --vss, nó sẽ trông như thế này:



Và trong trường hợp này, KAPE đã tìm và xử lý thêm hàng trăm tệp tìm nạp trước từ các VSC, sao chép chúng ra và chạy PECmd đối với chúng trong 5,8383 giây.

Các tùy chọn hữu ích khác
Công tắc --debug và --trace có thể được sử dụng khi viết các mục tiêu và mô-đun của riêng bạn cũng như cho những thứ như chỉ báo tiến trình trên các liên kết chậm hơn. 

--debug thêm thông tin về các tệp được tìm thấy, sao chép, v.v.




--trace thêm nhiều chi tiết hơn nữa vào đầu ra, bao gồm những gì KAPE đã mở rộng các mục tiêu và mô-đun, v.v.





Để xem mức độ hoạt động của KAPE, hãy chạy KAPE một vài lần với cả --debug và --trace được bật, sau đó xem lại tệp ConsoleLog so với khi không sử dụng công tắc nào.


Kết hợp các mục tiêu và mô-đun
Như chúng ta đã thấy ở trên, KAPE có thể sử dụng tùy chọn Mục tiêu hoặc tùy chọn Mô-đun. Người này không dựa vào người kia. Tuy nhiên, cả hai tùy chọn có thể được sử dụng cùng một lúc. Về cơ bản, điều này cho phép bạn xây dựng "chuỗi thu thập và xử lý" của riêng mình để có thể làm bất cứ điều gì bạn muốn.

Ví dụ: giả sử bạn muốn thu thập danh sách tìm nạp trước, tổ ong Đăng ký và nhảy, sau đó chạy PECmd, RECmd, JLECmd và Plaso để tạo siêu thời gian. Bạn có thể thực hiện điều này rất dễ dàng bằng cách xây dựng một Mục tiêu kéo các tệp cần thiết, sau đó xây dựng Mô-đun gọi các mô-đun thích hợp để chạy các chương trình nói trên.

Dòng lệnh có thể trông như thế này:

kape.exe --tsource c: --tdest L:\collect --target QuickTimeline --mdest L:\output --module QuickTimeline

Chuyện gì đang xảy ra ở đây vậy? Mục tiêu và mô-đun "QuckTimeline" đến từ đâu? Rất đơn giản, bạn tạo ra nó! Hãy nhớ rằng các tệp cấu hình mô-đun và mục tiêu chỉ là YAML, do đó, sử dụng trình soạn thảo văn bản yêu thích của bạn, tạo một bản sao của mục tiêu hiện có (chẳng hạn như mục tiêu WebBrowsers), sau đó cập nhật tệp mới để trỏ đến các mục tiêu khác mà bạn muốn, như sau:




Bắt đầu với một trong các tệp mô-đun được bao gồm, mô-đun mới của chúng tôi sẽ được xử lý theo cùng một cách:





Với mục tiêu và mô-đun tại chỗ, chúng tôi sẽ chỉ chạy KAPE như trong ví dụ trên và KAPE sẽ thực hiện phần còn lại!

Trước tiên, KAPE sẽ tìm và sao chép tất cả các tệp dựa trên tệp Đích, sao chép tất cả chúng vào L:\collect, sau đó gọi từng bộ xử lý đối với các tệp trong L:\collect. Đầu ra từ mỗi chương trình sẽ được lưu vào L:\output chứa các thư mục cho từng danh mục. Các tệp CSV trong các thư mục này có thể được tải vào Timeline Explorer và được phân tích, tất cả chỉ trong vòng vài giây!

Chạy lệnh này có thể trông như thế này:




Rất nhiều điều này chúng ta đã thấy trước đây, nhưng trong trường hợp của tôi, hãy lưu ý rằng tôi không có tệp nhị phân ở đúng vị trí để mô-đun plaso hoạt động bình thường. Trong trường hợp này, KAPE cho chúng ta biết đây là trường hợp, nhưng nó không khiến KAPE không hoạt động bình thường.

Điều khác cần lưu ý ở đây là một số bộ xử lý khác đã được tìm thấy và thực thi. 

Trong trường hợp này, --mdest sẽ trông như thế này:





Các trường hợp sử dụng khác
KAPE có các tùy chọn đặc biệt, chẳng hạn như %d , có thể được sử dụng trên dòng lệnh cho đường dẫn đích và mô-đun đích, như sau:

kape.exe --tsource c: --tdest L:\collect%d --target EvidenceOfExecution--mdest L:\output%d --module PECmd

Đầu tiên, lưu ý rằng chúng tôi KHÔNG chỉ định --msource. Khi --msource không được cung cấp trên dòng lệnh, nó được kế thừa từ giá trị của --tdest. Bạn có thể thấy tại sao điều này lại cần thiết khi sử dụng %d, bởi vì bạn sẽ không biết trước tên của thư mục sẽ sử dụng cho --msource. =)

Vì vậy, cái này đang làm gì? Khi KAPE chạy, nó sẽ thay thế %d bằng dấu thời gian ở dạng YYYYMMddHHmmss, vì vậy kết quả thực sự của chúng tôi sẽ là:

L:\Collect20190213113605

và

L:\Output20190213113605

Lưu ý rằng dấu thời gian cũng khớp trên mỗi thư mục.

Sử dụng phương pháp này, bạn có thể sử dụng tác vụ đã lên lịch để tự động sao chép và xử lý bất kỳ tệp nào bạn muốn trong bất kỳ khoảng thời gian nào bạn muốn (có thể kết xuất tìm nạp trước mỗi giờ vào thư mục gốc và KAPE sẽ xử lý việc thêm dấu thời gian).

Nếu bạn đã xem nhà bếp thử nghiệm của Dave Cowen và thấy anh ấy định vị và trích xuất các tệp theo cách thủ công với các tên khác nhau, hãy xem xét khả năng sử dụng KAPE và mục tiêu Syscache để tự động thu thập các tổ ong Registry có liên quan và các tệp khác cứ sau 15 phút (hoặc theo yêu cầu, bằng cách lặp lại lệnh), sau đó so sánh nội dung của từng lệnh để tìm trình kích hoạt khi cập nhật xảy ra.

Quá trình này cũng có thể được sử dụng để tự động tìm và đóng gói các tệp bằng chứng VHDX theo thời gian bằng cách ghi vào ổ đĩa Google chỉ đọc hoặc chia sẻ Dropbox, v.v. Nói cách khác, bạn có thể tạo các bộ dữ liệu mẫu về tổ ong Registry, tìm nạp trước, dữ liệu hệ thống tệp, v.v. vào các bộ chứa VHDX để mọi người kiểm tra các công cụ của họ, xác thực các công cụ, v.v.

Một tình huống khác là cần chia sẻ Registry hives với ai đó. Bạn có thể sử dụng mục tiêu RegistryHives cùng với --vhdx và trong vài giây, bạn có một gói đẹp để gửi cho bất kỳ ai cần.

Các trường hợp sử dụng là không giới hạn và điều này thực sự chỉ là bề nổi của những gì có thể.


Và cuối cùng, nhưng không kém phần quan trọng, làm cho nó dễ sử dụng hơn.
KAPE thực chất là một công cụ dòng lệnh và không khó để sử dụng khi bạn đã biết những điều cơ bản. 

Như đã nói, KAPE có một chương trình trợ giúp thứ cấp, gkape, bao bọc phiên bản dòng lệnh và làm cho nó dễ sử dụng và làm quen hơn. 

Giao diện chính trông như thế này:



Khi các tùy chọn được bật, các phần khác sẽ mở ra. Ở đây, chúng ta thấy mọi thứ thay đổi như thế nào khi các tùy chọn mô-đun và mục tiêu được chọn và một số thuộc tính bắt buộc (được viền màu đỏ ) được điền:




Khi các tùy chọn được điền, dòng lệnh được tạo ở dưới cùng. Tiếp tục chọn các tùy chọn cần thiết, chúng tôi sẽ kết thúc với điều này:




Khi một dòng lệnh hợp lệ được tạo, nút lệnh Thực thi và Sao chép được bật. 

Nhấp vào Thực thi sẽ chạy KAPE trong một cửa sổ mới:




Và tất cả các khía cạnh khác của KAPE đều hoạt động theo cùng một cách. Truy cập một hoặc cả hai --tdest và --mdest sẽ hiển thị cho bạn tất cả các tệp KAPE đã thu thập và xử lý.

KAPE hiện có sẵn miễn phí cho tất cả mọi người!


Cuối cùng, có một kho lưu trữ GitHub công khai, nằm tại  https://github.com/EricZimmerman/KapeFiles mà bạn có thể kéo các yêu cầu vào nếu bạn viết các mục tiêu và mô-đun hữu ích và muốn chia sẻ chúng với cộng đồng (VUI LÒNG LÀM!)
