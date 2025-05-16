<h1>Questions: What are some differences between interfaces and types in TypeScript?</h1>

Answer: I think interfaces and types are both very important in TypeScript because they help users understand and define structures easily. While interfaces and types are similar, there are some key differences. Let’s look at them.
Declaration:
Interfaces use the interface keyword, while types use the type keyword for declaration.
example: 
interface Person {
  name: string;
  age: number;
}

type Employee = {
  name: string;
  age: number;
};

Extensibility:
Interfaces can be extended using extends, while types use the & (intersection) operator.
Example: 
interface Person {
  name: string;
}

interface Developer extends Person {
  language: string;
}

type PersonType = {
  name: string;
};

type DeveloperType = PersonType & {
  language: string;
};

Merging:
Interfaces with the same name in the same scope will be merged automatically. However, types with the same name will cause a compiler error.
Example:
interface Animal {
  legs: number;
}

interface Animal {
  tail: boolean;
}

const dog: Animal = { legs: 4, tail: true };

type Plant = {
  name: string;
};


Capabilities:
Both interfaces and types can define object shapes, but types are more flexible. Types can define unions, tuples, and other complex structures that interfaces cannot.
Example: 
type Status = "loading" | "success" | "error";
type Point = [number, number];


Use Cases:
Interfaces are commonly used for defining object shapes and classes. Types are preferred when creating aliases for complex types or primitive unions.
Example:
interface User {
  username: string;
  email: string;
}

type ApiResponse = User | { error: string };

type ID = string | number;



Questions: What is the use of the keyof keyword in TypeScript? Provide an example.

Answer: The keyof keyword is used to get a union of all property names (keys) of a type or interface. It returns the keys as a string literal type. keyof is useful when you want to access object properties dynamically in a type-safe way.
Example: 
interface Product {
  name: string;
  price: number;
}


type ProductKeys = keyof Product; // "name" | "price"


function getValue<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

const item: Product = {
  name: "Laptop",
  price: 1200,
};

const value = getValue(item, "price");
