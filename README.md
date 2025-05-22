# Hottel-Managment

@startuml
' Package model
package model {
  class Booking {
    - int bookingId
    - UserInfo customer
    - ArrayList<Room> rooms
    - long checkInDateTime
    - long checkOutDateTime
    - String bookingType
    - int numberOfGuests
    + addRoom(r: Room)
    + getRooms(): ArrayList<Room>
    + getBookingId(): int
    + setBookingId(id: int)
  }

  class UserInfo {
    - String name
    - String contactDetails
    + getName(): String
    + setName(name: String)
  }

  class Room {
    - int roomId
    - String roomType
    + getRoomId(): int
    + setRoomType(type: String)
  }

  class Food {
    - int foodId
    - String foodName
    + getFoodId(): int
    + setFoodName(name: String)
  }

  class Item {
    - int itemId
    - String itemName
    + getItemId(): int
    + setItemName(name: String)
  }

  class Order {
    - int orderId
    - ArrayList<Item> items
    + addItem(item: Item)
    + getItems(): ArrayList<Item>
  }

  class Payment {
    - int paymentId
    - double amount
    + getAmount(): double
    + setAmount(amount: double)
  }
}

' Package database
package database {
  class BookingDb {
    + saveBooking(b: Booking)
    + getBookingById(id: int): Booking
  }
  class CustomerDb {
    + saveCustomer(u: UserInfo)
  }
  class DataBaseConnection {
    - static instance: DataBaseConnection
    + getInstance(): DataBaseConnection
    + connect()
  }
}

' Package controller
package controller {
  class DatabaseOperation {
    + saveBooking(b: Booking)
    + fetchAllBookings(): List<Booking>
  }
}

' Package ui
package ui {
  class ControlPanel {
    + display()
  }
  class CustomerPanel {
    + display()
  }
  class FoodPanel {
    + display()
  }
  class OrderPanel {
    + display()
  }
  class PaymentPanel {
    + display()
  }
  class RoomPanel {
    + display()
  }
}

