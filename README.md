#include <iostream>
#include <cmath>

// Base class for geometric shapes
class Shape {
public:
    // Virtual functions for area and perimeter
    virtual double area() const = 0;
    virtual double perimeter() const = 0;
};

// Circle class derived from Shape
class Circle : public Shape {
private:
    double radius;
public:
    // Constructor
    Circle(double r) : radius(r) {}
    
    // Overrides for area and perimeter
    double area() const override {
        return M_PI * radius * radius;
    }
    
    double perimeter() const override {
        return 2 * M_PI * radius;
    }
};

// Rectangle class derived from Shape
class Rectangle : public Shape {
private:
    double length;
    double width;
public:
    // Constructor
    Rectangle(double l, double w) : length(l), width(w) {}
    
    // Overrides for area and perimeter
    double area() const override {
        return length * width;
    }
    
    double perimeter() const override {
        return 2 * (length + width);
    }
};

// Triangle class derived from Shape
class Triangle : public Shape {
private:
    double side1;
    double side2;
    double side3;
public:
    // Constructor
    Triangle(double s1, double s2, double s3) : side1(s1), side2(s2), side3(s3) {}
    
    // Overrides for area and perimeter
    double area() const override {
        double s = (side1 + side2 + side3) / 2;
        return sqrt(s * (s - side1) * (s - side2) * (s - side3));
    }
    
    double perimeter() const override {
        return side1 + side2 + side3;
    }
};

int main() {
    // Example usage
    Circle circle(5);
    Rectangle rectangle(4, 6);
    Triangle triangle(3, 4, 5);
    
    std::cout << "Circle: Area = " << circle.area() << ", Perimeter = " << circle.perimeter() << std::endl;
    std::cout << "Rectangle: Area = " << rectangle.area() << ", Perimeter = " << rectangle.perimeter() << std::endl;
    std::cout << "Triangle: Area = " << triangle.area() << ", Perimeter = " << triangle.perimeter() << std::endl;
    
    return 0;
}
