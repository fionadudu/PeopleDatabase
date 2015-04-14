# PeopleDatabase

主要还是loop 的练习  。还有input() 练习。do{}while()练习。
总共三个part。1. helpers.swift  2. main.swift    3. Person.swift

### 1. Person.swift

import Foundation

class Person  {
  
  var firstName = ""
  
  var lastName = ""
  
  var age = 0
  

  func input() -> String {
  
    let keyboard = NSFileHandle.fileHandleWithStandardInput()
    
    let inputData = keyboard.availableData
    
    let rawString = NSString(data: inputData, encoding:NSUTF8StringEncoding)
    
    if let string = rawString {
    
      return string.stringByTrimmingCharactersInSet(NSCharacterSet.whitespaceAndNewlineCharacterSet())
      
    } else {
    
      return "Invalid input"
      
    }
    
  }
  

  func changeFirstName(newFirstName:String) {
  
    firstName = newFirstName
    
  }
  
  func enterInfo()  {
  
    println("What is the first name?")
    
    firstName = input()
    
    println("What is \(firstName)'s last name?")
    
    lastName = input()
    
    println("How old is \(firstName) \(lastName)")
    
    let userInput = input().toInt()
    
    if let number = userInput {
    
      age = number
      
    }
    
  }
  
  func printInfo()  {
  
    println("\(firstName) \(lastName) is \(age) years old")
    
  }
  
}

### 2. main.swift
import Foundation
var response: String
var people: [Person] = []

do {

  var newPerson = Person()
  
  newPerson.enterInfo()
  
  people.append(newPerson)
  
  newPerson.printInfo()
  
  println("Do you want to enter another name? (y/n)")
  
  response = input()
 
} while(response == "y")

println("Number of people in the database: \(people.count)")

for onePerson in people  {

  onePerson.printInfo()
  
}

### 3. helpers.swift
import Foundation

func input() -> String {

  let keyboard = NSFileHandle.fileHandleWithStandardInput()
  
  let inputData = keyboard.availableData
  
  let rawString = NSString(data: inputData, encoding:NSUTF8StringEncoding)
  
  if let string = rawString {
  
    return string.stringByTrimmingCharactersInSet(NSCharacterSet.whitespaceAndNewlineCharacterSet())
    
  } else {
  
    return "Invalid input"
    
  }
  
}

func randomIntBetween(low:Int, high:Int) -> Int {

  let range = high - (low - 1)
  
  return (Int(arc4random()) % range) + (low - 1)
  
}
