### Rule of thumb TLDR
Prefer composition over inheritance

### Inheritance
##### Definition
- class A {} class B : A {}
- class B will copy everything from class A
- class B can choose to override certain functions from class A
##### Use
- Copy all the methods and fields from a class
- Override methods
- Have a Base class from which you can call an overridden method of a bunch of different classes (abstract or not)
##### Examples
###### Image example (working)
```cpp
class Image
{
	void resize(double scale);
	void flip();
	void save() = 0;
	void load() = 0;
}

class PngImage : Image
{
	void save() override;
	void load() override;
}

class JpgImage : Image
{
	void save() override;
	void load() override;
}
```
###### Image gone wrong
```cpp
class Image
{
	void resize(double scale);
	void flip();
	void save() = 0;
	void load() = 0;
}

class PngImage : Image
{
	void save() override;
	void load() override;
}

class JpgImage : Image
{
	void save() override;
	void load() override;
}
class DrawableImage : Image
{
	void draw() override;
}
```

##### Takeaways

- #inheritance should be used for abstractization
- #composition should almost always be preferred when it comes to reusability
- #composition generates more boilerplate
- #inheritance deals badly with orthogonal features
- #inheritance is a "is-a" relationship while #composition is a "has-a" relationship
##### References
- https://www.youtube.com/watch?v=hxGOiiR9ZKg
- https://www.youtube.com/watch?v=0mcP8ZpUR38