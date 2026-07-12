# Garage Management System (C#)

A console-based garage management application written in C# as an object-oriented programming exercise. The emphasis is on clean OOP design: a clear separation between a logic class library (`Ex03.GarageLogic`) and a console UI project (`Ex03.ConsoleUI`), with the UI containing no business logic.

## Design Highlights

- **Inheritance hierarchies** — an abstract `Vehicle` base class extended by `Car`, `Motorcycle`, and `Truck`, each with its own type-specific properties (e.g., license type for motorcycles, hazardous cargo for trucks); an abstract `Engine` extended by `FuelEngine` and `ElectricEngine`, so refueling/recharging logic is polymorphic rather than type-switched.
- **Factory pattern** — `VehicleCreator` encapsulates vehicle construction, so adding a new vehicle type doesn't touch the UI or the `Garage` class.
- **Encapsulated domain state** — the `Garage` class manages `ClientInformation` records and vehicle status (`InRepair` / `Repaired` / `Paid`).
- **Input validation & custom exceptions** — a dedicated `ValidationCheck` layer and a custom `ValueOutOfRangeException` for range violations, keeping error handling consistent across the system.

## Features

Console menu supporting:

1. Register a new vehicle (with dynamic, type-specific questions)
2. Display license numbers, filterable by vehicle status
3. Change a vehicle's repair status
4. Inflate wheels to maximum air pressure
5. Refuel a fuel-based vehicle
6. Recharge an electric vehicle
7. Display full vehicle details by license number

## Project Structure

```
├── Ex03.GarageLogic.csproj   # class library: domain model & logic
│   ├── Vehicle.cs / Car.cs / Motorcycle.cs / Truck.cs
│   ├── Engine.cs / FuelEngine.cs / ElectricEngine.cs
│   ├── Garage.cs / VehicleCreator.cs
│   └── ValidationCheck.cs / ValueOutOfRangeException.cs
└── Ex03.ConsoleUI.csproj     # console front-end
    ├── Program.cs
    └── ConsoleManageGarage.cs
```

Full design documentation: [`CSharpGarage.pdf`](CSharpGarage.pdf).
