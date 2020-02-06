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
	PromotionName nvarchar(100),
	Discount int,
	DesPromotion nvarchar(50),
	UrlPicPromotion nvarchar(100),
	StartDate date,
	EndDate date,
	primary key (PromotionId)
);
create table Products (
	ProductId int identity(1,1),
	ProductName nvarchar(50),
	SupplierId int,
	CategoryId int,
	Origin nvarchar(50),
	Size int
);
create table SizeShoes(
	ProductId int,
	Size nvarchar(20),
	primary key(ProductId)
)
create table ColorShoes(
	ProductId int ,
	Color nvarchar(20),
	UrlImage nvarchar(100),
	primary key(ProductId)
);
create table ImageShoes(
	ProductId int ,
	UrlImage nvarchar(100),
	primary key(ProductId)
)


