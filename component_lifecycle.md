# Vòng đời React Component

## constructor(props)

- Được gọi khi một thể hiện của component được tạo ra.
- Có thể dùng để khởi tạo state cho component.
- Cũng có thể dùng để "bind" các hàm của component.
- Nếu phải cài đặt hàm này thì phải khai báo 1 tham số props cho nó và phải gọi super(props) đầu tiên.
- Nếu không làm gì thì không phải cài đặt hàm này.

## componentWillMount()

- Được gọi trước khi render().
- Dùng để đăng ký các sự kiện toàn cục.
- Dựa vào các props để tính toán và set lại state

## render()

- Hàm này bắt buộc phải có trong component().
- Trả về 1 đối tượng JSX (có thể lồng các đối tượng với nhau nhưng phải có 1 đối tượng gói tất cả các đối tượng lại) để hiển thị hoặc null / false nếu không muốn hiển thị gì.
- Không được gọi setState() trong hàm này (cũng như trong các hàm mà hàm này gọi đến), bởi khi gọi setState() thì hàm render sẽ được gọi => gây ra lặp vô hạn.

## componentDidMount()

- Ngay sau khi hàm render được gọi đến lần đầu tiên chạy xong thì hàm này sẽ được chạy.
- Thường dùng để fetch dữ liệu từ server và sau đó setState để render dữ liệu ra.
- Đến đây thì các phần tử đã được sinh ra rồi, và có thể tương tác với DOM bằng JS trong hàm này.

## componentWillReceiveProps(nextProps)

Hàm này được chạy khi mà props của component đã được sinh ra có sự thay đổi.
Phải gọi setState() nếu muốn render lại.

## shouldComponentUpdate(nextProps, nextState)

Được gọi trước render.
Trả về true / false. Nếu false thì sẽ không render lại. Mặc định là true.

## componentWillUpdate(nextProps, nextState)

Được gọi ngay sau shouldComponentUpdate() nếu hàm này trả về true.
Không gọi setState() trong hàm này bởi hàm này là để chuẩn bị update cho đối tượng chứ không phải tạo ra 1 update mới, sẽ tạo ra lặp vô hạn.
Hàm render sẽ được gọi ngay sau hàm này.

## componentDidUpdate(prevProps, prevState)

Được gọi ngay sau render() từ lần render thứ 2 trở đi.
Đây cũng là 1 cơ hội để thao tác với các phần tử DOM bằng JS.

## componentWillUnmount()

Được gọi khi 1 component được loại bỏ khỏi DOM.
Thực hiện các thao tác dọn dẹp như huỷ các timer, loại bỏ các phần tử thừa, ...
