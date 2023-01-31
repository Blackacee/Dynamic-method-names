# Dynamic-method-names

let METADATA = Symbol('metadata');
class Car {
 constructor(make, model) {
 this.make = make;
 this.model = model;
 }
 // example using symbols
[METADATA]() {
 return {
 make: this.make,
 model: this.model
 };
 }
 // you can also use any javascript expression
 // this one is just a string, and could also be defined with simply add()
 ["add"](a, b) {
 return a + b;
 }
 // this one is dynamically evaluated
 [1 + 2]() {
 return "three";
 }
}
let MazdaMPV = new Car("Mazda", "MPV");
MazdaMPV.add(4, 5); // 9
MazdaMPV[3](); // "three"
MazdaMPV[METADATA](); // { make: "Mazda", model: "MPV" }
