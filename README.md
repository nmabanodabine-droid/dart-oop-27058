# Dart OOP Assignment: Kigali Bus Card

**Name:** Nshuti Mabano Dabine
**Student ID:** 27058

## My numbers
D = 58
L = 8
Starting balance = 1580 RWF
Bus fare = 258 RWF
Student discount = 18%

## Output of main.dart
Owner: Nshuti Mabano Dabine | Balance: 1000 RWF
Error: top-up must be 500 to 50000 RWF
Topped up 2000 RWF
Paid 258 RWF
Paid 258 RWF
Owner: Nshuti Mabano Dabine | Balance: 2484 RWF
Student discount: 46 RWF
Paid 212 RWF
Owner: Nshuti Mabano Dabine | Balance: 1368 RWF
Student card: 18% off
PS C:\Users\HP\Downloads\dart-oop-27058> 

## Part 1: Why no setter for balance?
There is no setter for `balance` so code outside `BusCard` cannot set the balance directly to an invalid value or jump straight to a high balance. All changes to `_balance` must go through `topUp()` and `pay()`, which enforce the top-up limits and card balance check.

## Part 2: What does ~/ do?
`~/` is integer division in Dart. It divides two numbers and returns only the whole integer part, dropping any remainder or decimal fraction.
- `237 * 17 / 100` returns `40.29` (a `double` with decimals).
- `237 * 17 ~/ 100` returns `40` (an `int` with the decimal part removed).

## Part 4: Bug table
| Bug | The line | Why it is wrong (your words) | Your fix |
| --- | --- | --- | --- |
| 1 | `String _brand; int _battery;` | Non-nullable fields in `Phone` are not given initial values before the constructor runs. | Initialized them to `''` and `0`. |
| 2 | `SmartPhone (String brand, int battery, String system) {` | The child constructor does not pass `brand` and `battery` up to `Phone`'s constructor using `super`. | Added `: super(brand, battery)` to the constructor. |
| 3 | `_system = system;` | `_system` does not exist; the field on `SmartPhone` is named `system`. | Changed assignment to `this.system = system;`. |
| 4 | `@override void restart() {` | `Phone` has no `restart()` method, so `@override` cannot override a parent method. | Removed `@override` from `restart()`. |
| 5 | `p.battery = 100;` and `print(p.battery());` | `battery` only has a getter (no setter) so assigning `100` fails, and `battery` is a getter, not a method `battery()`. | Added `set battery(int value)` with `0` to `100` check and changed print to `print(p.battery);`. |
| Not a bug | `Phone p = new Phone ('Tecno', 50);` | This is valid Dart syntax for creating a `Phone` object with `brand` and `battery`. | (none) |

## Part 5
My prediction:
1
5

Real output:
1
5

Was I right?
Yes. `a.add()` increases `_items` to `1`, `a.items = -5` is ignored because `-5` is not `>= 0`, so `print(a.items)` outputs `1`. Then `b.add()` runs twice (each calling `super.add()` twice, adding `4` total), and `b.items = b.items + 1` sets it to `5`, so `print(b.items)` outputs `5`.