# FxSound

**FxSound** — это программа для обработки цифрового звука, созданная для компьютеров под управлением `Windows`

Фоновая обработка, построенная на аудиодвижке высокого качества, работает как своего рода виртуальная звуковая карта для вашей системы. Это означает, что при активной работе `FxSound` сигналы будут проходить через систему с чистым, неискажённым звуком.

Помимо такой чистой обработки, в программе есть активные эффекты для формирования и усиления громкости, тембра и эквалайзера звука — это позволяет настраивать и улучшать звучание по своему вкусу.

## Общая информация

- **Сайт:** [fxsound.com](https://www.fxsound.com)
- **Установщик:** [скачать последнюю версию](https://download.fxsound.com/fxsoundlatest)
- **Исходный код:** [GitHub](https://github.com/fxsound2/fxsound-app)
- **Трекер проблем (issues):** [GitHub Issues](https://github.com/fxsound2/fxsound-app/issues)
- **Форум:** [forum.fxsound.com](https://forum.fxsound.com)
- **Поддержать проект пожертвованием:** [PayPal](https://www.paypal.com/donate/?hosted_button_id=JVNQGYXCQ2GPG)

## Документация

- [Параметры командной строки](docs/COMMAND_LINE_OPTIONS.md)

## Инструкции по сборке

### Предварительные требования

- Скачайте и установите [последнюю версию FxSound](https://download.fxsound.com/fxsoundlatest). Это нужно, чтобы установился виртуальный аудиодрайвер `FxSound Audio Enhancer` — он обязателен для работы приложения.
- Установите [Visual Studio 2022](https://visualstudio.microsoft.com/vs)
- Установите [Windows SDK](https://developer.microsoft.com/en-us/windows/downloads/windows-sdk)
- Установите [JUCE 6.1.6](https://github.com/juce-framework/JUCE/releases/tag/6.1.6) для платформ `x64/x86`
- **Для ARM64:** установите [последнюю версию фреймворка JUCE](https://api.juce.com/api/v1/download/juce/latest/windows)

### Сборка FxSound в Visual Studio

1. **Откройте решение:** файл `fxsound/Project/FxSound.sln` из репозитория [fxsound-app](https://github.com/fxsound2/fxsound-app/blob/main/fxsound/Project/FxSound.sln) в `Visual Studio`
2. Соберите нужную конфигурацию и платформу (например, `Release/x64`).
3. Запустите проект.

### Сборка после экспорта проекта из Projucer

**Приложение `FxSound` состоит из трёх компонентов:**

1. **FxSound GUI** — графическое приложение на фреймворке `JUCE`
2. **Audiopassthru** — модуль для взаимодействия с аудиоустройствами.
3. **DfxDsp** — DSP‑модуль для обработки аудиосигнала.

Из‑за ограничений `Projucer` при экспорте в `Visual Studio` некоторые зависимости не добавляются автоматически.

**Чтобы сборка прошла успешно, выполните следующие шаги:**

1. В открытом решении `FxSound.sln` вручную добавьте проекты: `audiopassthru/audiopassthru.vcxproj` и `dsp/DfxDsp.vcxproj`
2. В проекте `FxSound_App` добавьте ссылки (references) на проекты `audiopassthru` и `DfxDsp`
3. Если запускаете из `Visual Studio` и хотите, чтобы приложение использовало пресеты, задайте рабочую директорию:  
   В свойствах проекта `FxSound_App` → Properties → Debugging → Working Directory укажите: `(SolutionDir)..\..\bin\(PlatformTarget)`


## Как внести вклад в проект

Мы рады любым желающим поучаствовать в развитии проекта. Подробнее о том, как внести свой вклад, читайте в [руководстве для участников](./CONTRIBUTING.md).

## Благодарности

- **Advanced Installer** — за предоставление лицензии Advanced Installer Professional для сборки установщика.
- **JUCE** — фреймворк, используемый в проекте (лицензия AGPL v3.0): [juce.com](https://juce.com).
- **Theremino** — за ценный вклад и реализацию важных улучшений в FxSound: [theremino.com](https://www.theremino.com).

![Advanced Installer logo](https://github.com/user-attachments/assets/c133fe06-619c-4c17-bce9-f1cf051c5265)

## Лицензия

Проект распространяется под лицензией [AGPL v3.0](https://github.com/fxsound2/fxsound-app/blob/main/LICENSE).

