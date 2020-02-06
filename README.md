# document
create database OnlineShoesShop

Use [OnlineShoesShop]
go

create table RoleUser(
	RoleId int identity(1,1),
	RoleName nvarchar(50) not null,
	Description nvarchar(100) not null,
	primary key (RoleId)
);

create table UserAcount(
	UserId int identity(1,1),
	RoleId int not null,
	FullName nvarchar(100) not null,
	Gender bit not null,
	UrlAvatar nvarchar(200),
	DateOfBirth Date not null,
	Email nvarchar(50) not null,
	PhoneNumber nvarchar(15) not null,
	AddressHome nvarchar(100) not null,
	Country nvarchar(20),
	Password nvarchar(50) not null,
	primary key (UserId),
	foreign key (RoleId) references RoleUser(RoleId)
);

create table Supplier(
	SupplierId int identity(1,1),
	SupplierName nvarchar(100) not null,
	Summary nvarchar(500) not null,
	UrlLogo nvarchar(200) not null,
	AddressCompany nvarchar(100) not null,
	Country nvarchar(20) not null,
	Phone nvarchar(20) not null,
	Fax nvarchar(50) not null,
	PostalCode nvarchar(20) not null,
	HomPage nvarchar(50) ,
	primary key(SupplierId)
);

create table Categories (
	CategoryId int identity(1,1),
	CategoryName nvarchar(100) not null,
	Description nvarchar(200) not null,
	primary key (CategoryId)
);
create table Promotion (
	PromotionId int identity(1,1),
	PromotionName nvarchar(100) not null,
	Discount int not null,
	DesPromotion nvarchar(50) not null,
	UrlPicPromotion nvarchar(100) not null,
	StartDate date not null,
	EndDate date not null,
	primary key (PromotionId)
);
create table Products (
	ProductId int identity(1,1),
	ProductName nvarchar(50) not null,
	PromotionId int not null,
	SupplierId int not null,
	CategoryId int not null,
	Origin nvarchar(50) not null,
	Price decimal not null,
	primary key(ProductId),
	foreign key (PromotionId) references Promotion(PromotionId)
);
create table SizeShoes(
	ProductId int not null,
	Size int not null,
	primary key(ProductId),
	foreign key (ProductId) references Products(ProductId)
)
create table ColorShoes(
	ProductId int not null,
	Color nvarchar(20) not null,
	UrlImage nvarchar(100) not null,
	primary key(ProductId),
	foreign key (ProductId) references Products(ProductId)
);
create table ImageShoes(
	ProductId int not null,
	UrlImage nvarchar(100) not null,
	primary key(ProductId),
	foreign key (ProductId) references Products(ProductId)
)
create table Orders(
	OrderId int identity(1,1),
	UserId int not null,
	OrderDate datetime not null,
	DeliveryDate date not null,
	DeliveryCharge float not null,
	primary key(OrderId),
	foreign key (UserId) references UserAcount(UserId)
);
create table OrdersDetails(
	OrderId int not null,
	ProductId int not null,
	Price decimal not null,
	Size int not null,
	Color nvarchar(20) not null,
	Discount int ,
	primary key (OrderId,ProductId),
	foreign key (ProductId) references Products(ProductId),
	foreign key (OrderId) references Orders(OrderId)
);

