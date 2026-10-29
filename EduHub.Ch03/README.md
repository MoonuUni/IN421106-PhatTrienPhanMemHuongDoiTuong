# Ch03 — Clean Architecture + REST API: EduHub Skeleton

Starter của Bài tập Ch03. Hoàn thành các đoạn `// TODO` (đánh số 1 đến 8), thêm 1 test mới, rồi nộp bằng Pull Request.
Yêu cầu đầy đủ và thang điểm: xem `de-bai.html` và `rubric.html` trong thư mục cha.

## Cấu trúc

```
EduHub.Domain/          Entity + interface repository (không phụ thuộc lớp nào)
EduHub.Application/     Handler của từng use case (phụ thuộc Domain)
EduHub.Infrastructure/  Repository lưu trong bộ nhớ (phụ thuộc Application)
EduHub.API/             Controller, Swagger, Program.cs (phụ thuộc Application + Infrastructure)
EduHub.Tests/           Unit test lớp Application, mock repository bằng Moq
```

## Danh sách TODO

| TODO | Tệp | Việc cần làm |
|---|---|---|
| 1a–1e | `EduHub.Infrastructure/Repositories/InMemoryClubRepository.cs` | 5 phương thức của kho CLB |
| 2 | `EduHub.Application/Clubs/GetClubsQuery.cs` | Handler lấy danh sách |
| 3 | `EduHub.Application/Clubs/GetClubByIdQuery.cs` | Handler lấy theo Id |
| 4a–4d | `EduHub.Application/Clubs/CreateClubCommand.cs` | Kiểm tra tên, tạo và lưu CLB |
| 5 | `EduHub.Application/Clubs/DeleteClubCommand.cs` | Handler xoá |
| 6a–6c | `EduHub.API/Program.cs` | Đăng ký DI |
| 7 | `EduHub.API/Program.cs` | Cấu hình Swagger |
| 8a–8i | `EduHub.API/Controllers/ClubsController.cs` | 4 endpoint và status code |

## Chạy

### Visual Studio

Mở file `EduHub.sln`, sau đó trong **Solution Explorer** nhấp chuột phải vào
`EduHub.API` và chọn **Set as Startup Project**. Project `EduHub.API` là
ASP.NET Core executable; các project còn lại là class library hoặc test project
và không thể chạy trực tiếp.

Có thể kiểm tra lại trong **Solution > Properties > Common Properties >
Startup Project** rằng **Single startup project** đang là `EduHub.API`. Nhấn
`F5` hoặc `Ctrl+F5` để chạy, rồi mở `/swagger` theo URL được Visual Studio
hiển thị.

### .NET CLI

```bash
dotnet build EduHub.sln
dotnet test
dotnet run --project EduHub.API
```

Sau khi thêm test thứ 5 (lấy CLB theo Id, mock bằng Moq), `dotnet test` phải báo 5 passed.
Không sửa 4 test có sẵn.

## Quy ước nộp bài

- Làm trên nhánh riêng (ví dụ `feature/ch03-skeleton`), commit theo Conventional Commits: `feat(club): ...`, `test(club): ...`.
- Tạo Pull Request về `main`, mô tả đủ what, why, how to test.
