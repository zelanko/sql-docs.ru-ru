---
title: 'Шаг 1: Настройка среда разработки для Ruby | Документы Microsoft'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8cdbadeb-f640-406c-977c-d2d44b7b5368
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eb14bee9528ad23b212bb0a7ffbbba02e1c39678
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35309703"
---
# <a name="step-1-configure-development-environment-for-ruby-development"></a>Шаг 1: Настройка среда разработки для Ruby
Необходимо будет настроить среду разработки с необходимых компонентов для разработки приложений с помощью драйвера Ruby для SQL Server.    
  
Обратите внимание, что драйвер Ruby использует протокол потока табличных данных, включенный по умолчанию в SQL Server и базы данных SQL Azure.  Дополнительная настройка не требуется.  
  
  
## <a name="windows"></a>Windows  
  
1.  **Загрузка установщика Ruby**  
Если компьютер не имеет Ruby установите ее. Для новых пользователей ruby мы рекомендуем использовать Ruby 2.2.X установщиков. Они предоставляют стабильный языка и обширный список пакетов (gems), которые совместимы и обновленный. Go [страницы загрузки Ruby](http://rubyinstaller.org/downloads/) и загрузить соответствующий 2.1.x установщик. Для примера при работе в 64-разрядном компьютере, загрузите установщик Ruby 2.1.6 (x 64).   
  
2.  **Установка Ruby**  
Когда программа установки загружается, выполните следующее:  
A. Дважды щелкните файл, чтобы запустить программу установки.  
Б. Выберите язык и согласиться с условиями.  
в.  На экране параметров установки установите флажки рядом с обоих исполняемые файлы Ruby, добавить к пути и связывать .rb .rbw файлы и Ruby установки.  
  
3.  **Загрузить набор Ruby разработки**  
Загрузить набор разработки RubyInstaller страницы  
  
4.  **Установите набор Ruby разработки**  
После завершения загрузки выполните следующие действия.  
A. Дважды щелкните файл. Вы получите запрос where, чтобы извлечь файлы.  
Б. Нажмите кнопку «...» и выберите «C:\DevKit». Возможно, потребуется сначала создать ее, нажав кнопку «Создать папку».  
в. Нажмите кнопку «ОК», а затем «извлечь», чтобы извлечь файлы.  
  
5. **Откройте cmd.exe**  
  
6. **Инициализировать Ruby набор разработки**  
```  
> chdir C:\DevKit  
> ruby dk.rb init  
> ruby dk.rb install  
```  
  
7.  **Установка TinyTDS gem**  
```  
> gem inst tiny_tds
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Откройте терминалов**  
  
2. **Установить диспетчер версий Ruby (rvm) и необходимые компоненты**  
```  
> sudo apt-get --assume-yes update  
> command curl -sSL https://rvm.io/mpapis.asc | gpg --import -  
> curl -L https://get.rvm.io | bash -s stable  
> source ~/.rvm/scripts/rvm  
```  
   
3. **Используется для установки Ruby rvm**  
Например можно установите версию 2.3.0 Ruby.  
```  
> rvm install 2.3.0  
> rvm use 2.3.0 --default  
> ruby -v  
```  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Убедитесь, что выходные данные последней команды указывает, что вы используете версию 2.3.0.  
  
4.  **Установить FreeTDS**  
```  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
```  
  
5.  **Установить TinyTDS**  
```  
> gem install tiny_tds  
```  
  
## <a name="mac"></a>Mac  
  
Обратите внимание, что Mac OS X уже Ruby предварительно установленной ОС имеет зависимость.    
  
1.  **Откройте терминалов**  
  
2. **Установка диспетчера пакетов Homebrew**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
3.  **Установить FreeTDS**  
```  
> brew install FreeTDS  
```  
  
4.  **Установка TinyTDS gem**  
```  
> gem install tiny_tds  
```
