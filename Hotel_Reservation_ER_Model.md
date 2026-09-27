# Hotel Reservation Management System -- ER Model

## 1. Entities and Attributes

### CUSTOMER

-   **Customer_ID (PK)**
-   Name
-   Phone
-   Email

### RESERVATION

-   **Reservation_ID (PK)**
-   Customer_ID (FK)
-   Room_ID (FK)
-   Check_In_Date
-   Check_Out_Date
-   Booking_Status

### PAYMENT

-   **Payment_ID (PK)**
-   Reservation_ID (FK)
-   Amount
-   Payment_Date
-   Payment_Method

### ROOM

-   **Room_ID (PK)**
-   Room_No
-   Room_Type
-   Price
-   Status
-   Hotel_ID (FK)

### ROOM_TYPE

-   **Room_Type_ID (PK)**
-   Type_Name
-   Capacity
-   Price

### HOTEL

-   **Hotel_ID (PK)**
-   Hotel_Name
-   Location
-   Contact_No

### STAFF

-   **Staff_ID (PK)**
-   Hotel_ID (FK)
-   Name
-   Role
-   Phone

### RESERVATION_SERVICE

-   **Reservation_ID (PK, FK)**
-   **Service_ID (PK, FK)**
-   Quantity
-   Service_Date

### SERVICE

-   **Service_ID (PK)**
-   Service_Name
-   Cost

------------------------------------------------------------------------

## 2. Relationships

  Entity 1              Relationship   Entity 2              Cardinality
  --------------------- -------------- --------------------- -------------
  Customer              Makes          Reservation           1 : M
  Reservation           Reserves       Room                  M : 1
  Reservation           Has            Payment               1 : 1
  Hotel                 Contains       Room                  1 : M
  Room                  Has            Room Type             M : 1
  Hotel                 Employs        Staff                 1 : M
  Hotel                 Uses           Reservation_Service   M : N
  Reservation_Service   Provides       Service               M : 1

------------------------------------------------------------------------

## 3. Simple ER Structure

``` text
CUSTOMER
   |
   | 1 : M
   | Makes
   v
RESERVATION -------- 1 : 1 -------- PAYMENT
   |
   | M : 1
   | Reserves
   v
 ROOM
   |    |  \ M : 1
   |   \ Has
   |    v
   |  ROOM_TYPE
   |
   | M : 1
   | Belongs to
   v
 HOTEL -------- 1 : M -------- STAFF
   |
   | M : N
   | Uses
   v
RESERVATION_SERVICE
   |
   | M : 1
   | Provides
   v
SERVICE
```

## 4. Keys

-   **PK** = Primary Key
-   **FK** = Foreign Key

## 5. Relationship Summary

-   One customer can make many reservations.
-   Many reservations can reserve one room.
-   One reservation has one payment.
-   One hotel contains many rooms.
-   Many rooms belong to one hotel.
-   Many rooms can have one room type.
-   One hotel employs many staff members.
-   Hotel and Reservation_Service have an M:N relationship.
-   Many Reservation_Service records can refer to one service.
