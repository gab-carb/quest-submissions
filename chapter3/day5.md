Chapter 3 Day 5 - Access Control

For today's quest, you will be looking at a contract and a script. You will be looking at 4 variables (a, b, c, d) and 3 functions (publicFunc, contractFunc, privateFunc) defined in SomeContract. In each AREA (1, 2, 3, and 4), I want you to do the following: for each variable (a, b, c, and d), tell me in which areas they can be read (read scope) and which areas they can be modified (write scope). For each function (publicFunc, contractFunc, and privateFunc), simply tell me where they can be called.

access(all) contract SomeContract {
    pub var testStruct: SomeStruct

    pub struct SomeStruct {

        //
        // 4 Variables
        //

        pub(set) var a: String

        pub var b: String

        access(contract) var c: String

        access(self) var d: String

        //
        // 3 Functions
        //

        pub fun publicFunc() {}

        access(contract) fun contractFunc() {}

        access(self) fun privateFunc() {}


        pub fun structFunc() {
            /**************/
            /*** AREA 1 ***/
            /**************/
            
            // a = Read/ Write
            // b = Read/ Write
            // c = Read/ Write
            // d = Read/ Write
            // publicFunc = Yes
            // contractFunc = Yes
            // privateFunc = Yes
            
        }

        init() {
            self.a = "a"
            self.b = "b"
            self.c = "c"
            self.d = "d"
        }
    }

    pub resource SomeResource {
        pub var e: Int

        pub fun resourceFunc() {
            /**************/
            /*** AREA 2 ***/
            /**************/
            
            // a = Read/ Write
            // b = Read/ No
            // c = Read/ No
            // d = No/No
            // e = Read/ Write
            // publicFunc = Yes
            // contractFunc = Yes
            // privateFunc = No
        }

        init() {
            self.e = 17
        }
    }

    pub fun createSomeResource(): @SomeResource {
        return <- create SomeResource()
    }

    pub fun questsAreFun() {
        /**************/
        /*** AREA 3 ****/
        /**************/
        
        // a = Read/ Write
        // b = Read/ No
        // c = Read/ No
        // d = No/ No
        // publicFunc = Yes
        // contractFunc = Yes
        // privateFunc = No
    }

    init() {
        self.testStruct = SomeStruct()
    }
}
This is a script that imports the contract above:

import SomeContract from 0x01

    pub fun main() {
     /**************/
    /*** AREA 4 ***/
    /**************/
    
    // a = Read/ No writing in a script
    // b = Read/ No writing in a script
    // c = No/ No writing in a script
    // d = No/ No writing in a script
    // publicFunc = Yes
    // contractFunc = No
    // privateFunc = No

    }
