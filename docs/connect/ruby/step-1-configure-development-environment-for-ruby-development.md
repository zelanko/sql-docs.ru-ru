---
title: Шаг 1. Настройка среды разработки для Ruby
description: Узнайте, как настроить среду разработки для Ruby.
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8cdbadeb-f640-406c-977c-d2d44b7b5368
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 700b0c1979b0eccc1544afb59296fba867e24c53
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81634593"
---
# <a name="step-1-configure-development-environment-for-ruby-development"></a>Шаг 1. Настройка среды разработки для разработки на языке Ruby
Чтобы разработать приложение с помощью драйвера Ruby для SQL Server, необходимо настроить среду разработки, учитывая необходимые условия.    
  
Драйвер Ruby использует протокол TDS, включенный по умолчанию в SQL Server и Базу данных SQL Azure.  Дополнительная настройка не требуется.  
  
  
## <a name="windows"></a>Windows  
  
1.  **Скачайте установщик Ruby**  
Если на вашем компьютере не установлен язык Ruby, установите его. Для новых пользователей Ruby рекомендуется использовать установщики Ruby 2.2.X, которые предоставляют стабильный язык и обширный список совместимых и обновленных пакетов (gems). Перейдите на [страницу загрузки Ruby](https://rubyinstaller.org/downloads/) и скачайте соответствующий установщик 2.1.x. Например, если вы используете 64-разрядный компьютер, скачайте установщик Ruby 2.1.6 (x64).   
  
2.  **Установите Ruby**  
Завершив скачивание установщика, выполните следующие шаги:  
а. Дважды щелкните файл установщика, чтобы запустить его.  
b. Выберите язык и примите условия.  
c.  На экране параметров установите флажки рядом с параметром "Добавить исполняемые файлы Ruby в путь" и "Связать файлы `.rb` и `.rbw` с этой установкой Ruby".  
  
3.  **Скачайте набор разработки Ruby**  
Скачайте набор разработки со страницы RubyInstaller  
  
4.  **Установите набор разработки Ruby**  
После завершения загрузки выполните следующие действия:  
а. Дважды щелкните файл. Вам будет предложено извлечь файлы.  
b. Нажмите кнопку "..." и выберите "C:\DevKit". Вероятно, вам потребуется сначала создать эту папку, нажав кнопку "Создать папку".  
c. Нажмите кнопку "ОК", а затем "Извлечь", чтобы извлечь файлы.  
  
5. **Откройте cmd.exe**  
  
6. **Инициализируйте набор разработки Ruby**  
```  
> chdir C:\DevKit  
> ruby dk.rb init  
> ruby dk.rb install  
```  
  
7.  **Установите TinyTDS gem**  
```  
> gem inst tiny_tds
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Откройте терминал**  
  
2. **Установите диспетчер версий Ruby (`rvm`) и предварительные требования**  
```  
> sudo apt-get --assume-yes update  
> command curl -sSL https://rvm.io/mpapis.asc | gpg --import -  
> curl -L https://get.rvm.io | bash -s stable  
> source ~/.rvm/scripts/rvm  
```  
   
3. **Установите Ruby с помощью `rvm`**  
Например, установите версию Ruby 2.3.0:  
```  
> rvm install 2.3.0  
> rvm use 2.3.0 --default  
> ruby -v  
```  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Убедитесь, что выходные данные последней команды показывают, что вы используете версию 2.3.0.  
  
4.  **Установите FreeTD**S  
```  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
```  
  
5.  **Установите TinyTDS**  
```  
> gem install tiny_tds  
```  
  
## <a name="macos"></a>macOS  
  
Примечание. В macOS уже установлен Ruby, так как операционная система имеет зависимость.
  
1.  **Откройте терминал**  
  
2. **Установите диспетчер пакетов Homebrew**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
3.  **Установите FreeTDS**  
```  
> brew install FreeTDS  
```  
  
4.  **Установите TinyTDS gem**  
```  
> gem install tiny_tds  
```
