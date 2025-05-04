# Komponent prognozy pogody w Blazor

Ten projekt to prosty, interaktywny komponent Blazor, który demonstruje:

✅ Wyświetlanie danych w tabeli  
✅ Filtrowanie danych według temperatury (ciepłe dni)  
✅ Filtrowanie danych według nazwy miasta w czasie rzeczywistym  
✅ Przywracanie oryginalnych danych  

---

## 🚀 Funkcje

- **Wyświetla prognozę pogody** w tabeli z datą, temperaturą (°C i °F) oraz nazwą miasta.
- **Pokazuje liczbę ciepłych dni** (temperatura powyżej 15°C).
- **Pozwala filtrować dane:**
  - Klikając **„Pokaż ciepłe dni”** (pokazuje tylko dni z temperaturą >15°C)
  - Wpisując **nazwę miasta** w polu filtra (dynamiczne filtrowanie)
- **Przywraca oryginalną listę** klikając przycisk **„Przywróć”**.

---

## 🛠️ Technologie

- **Blazor Server** (`@rendermode InteractiveServer`)
- **C#**
- **Razor Pages**

---

## 📄 Opis kodu

Komponent dostępny jest pod ścieżką `/weather` i działa według następującej logiki:

- Przy inicjalizacji **generuje 10 losowych prognoz pogody** (z losowymi miastami i temperaturami).
- **Wyświetla tabelę prognoz.**
- Umożliwia filtrowanie prognoz:
  - Metodą **`WarmDaysFilter`** (tylko dni z temperaturą >15°C)
  - Metodą **`Input`** (filtrowanie po nazwie miasta podczas wpisywania)
- Umożliwia przywrócenie wszystkich danych metodą **`RestoreForecasts`**.

### Przykład fragmentu kodu odpowiedzialnego za wyświetlanie:

```csharp
@if (forecasts == null)
{
    <p><em>Ładowanie...</em></p>
}
else
{
    <!-- Tabela z prognozami -->
}

Każdy obiekt WeatherForecast zawiera:

```private class WeatherForecast
{
    public DateOnly Date { get; set; }
    public int TemperatureC { get; set; }
    public string? Summary { get; set; }
    public int TemperatureF => 32 + (int)(TemperatureC / 0.5556);
}
