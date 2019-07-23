---
title: Шаг 1. Настройка среды разработки для Ruby | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8cdbadeb-f640-406c-977c-d2d44b7b5368
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 38af92d3cb0354bc4b75131a349f6a1c26e90490
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67992461"
---
# <a name="step-1-configure-development-environment-for-ruby-development"></a>Шаг 1. Настройка среды разработки для разработки на языке Ruby
Чтобы разработать приложение, использующее драйвер Ruby для SQL Server, необходимо настроить среду разработки с помощью необходимых компонентов.    
  
Обратите внимание, что драйвер Ruby использует протокол TDS, который по умолчанию включен в SQL Server и базе данных SQL Azure.  Дополнительная настройка не требуется.  
  
  
## <a name="windows"></a>Windows  
  
1.  **Скачать установщик Ruby**  
Если на компьютере нет Ruby, установите его. Для новых пользователей Ruby рекомендуется использовать установщики Ruby 2.2. X. Они предоставляют стабильный язык и обширный список пакетов (драгоценных камней), которые совместимы и обновлены. Перейдите на [страницу скачивания Ruby](https://rubyinstaller.org/downloads/) и скачайте соответствующий установщик 2.1. x. Например, если вы используете 64-разрядный компьютер, скачайте установщик Ruby 2.1.6 (x64).   
  
2.  **Установить Ruby**  
После загрузки установщика выполните следующие действия.  
A. Дважды щелкните файл, чтобы запустить установщик.  
Б. Выберите язык и примите условия.  
в.  На экране параметры установки установите флажки рядом с параметром добавить исполняемые файлы Ruby в путь и свяжите файлы RB и РБВ с этой установкой Ruby.  
  
3.  **Скачать Ruby DevKit**  
Скачивание DevKit со страницы Рубинсталлер  
  
4.  **Установить Ruby DevKit**  
После завершения загрузки выполните следующие действия.  
A. Дважды щелкните файл. Вам будет предложено извлечь файлы.  
Б. Нажмите кнопку "..." и выберите "К:\девкит". Вероятно, вам потребуется сначала создать эту папку, нажав кнопку "создать папку".  
в. Нажмите кнопку "ОК", а затем "извлечь", чтобы извлечь файлы.  
  
5. **Открыть CMD. exe**  
  
6. **Инициализация Ruby DevKit**  
```  
> chdir C:\DevKit  
> ruby dk.rb init  
> ruby dk.rb install  
```  
  
7.  **Установить драгоценный камень TinyTDS**  
```  
> gem inst tiny_tds
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Открыть терминал**  
  
2. **Установить Диспетчер версий Ruby (РВМ) и предварительные требования**  
```  
> sudo apt-get --assume-yes update  
> command curl -sSL https://rvm.io/mpapis.asc | gpg --import -  
> curl -L https://get.rvm.io | bash -s stable  
> source ~/.rvm/scripts/rvm  
```  
   
3. **Установка Ruby с помощью РВМ**  
Например, установите версию 2.3.0 Ruby:  
```  
> rvm install 2.3.0  
> rvm use 2.3.0 --default  
> ruby -v  
```  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Убедитесь, что выходные данные последней команды показывают, что вы используете версию 2.3.0.  
  
4.  **Установка FreeTDS**  
```  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
```  
  
5.  **Установка TinyTDS**  
```  
> gem install tiny_tds  
```  
  
## <a name="mac"></a>Mac  
  
Обратите внимание, что Mac OS X уже имеет предварительно установленный Ruby, так как операционная система имеет зависимость.    
  
1.  **Открыть терминал**  
  
2. **Установка диспетчера пакетов Homebrew**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
3.  **Установка FreeTDS**  
```  
> brew install FreeTDS  
```  
  
4.  **Установить драгоценный камень TinyTDS**  
```  
> gem install tiny_tds  
```
