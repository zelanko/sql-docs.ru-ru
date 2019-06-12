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
manager: jroth
ms.openlocfilehash: ff03ce6ec79aede2e056f0154836e77970af9c50
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66800829"
---
# <a name="step-1-configure-development-environment-for-ruby-development"></a>Шаг 1. Настройка среды разработки для разработки на языке Ruby
Необходимо будет настроить среду разработки с предварительными требованиями, чтобы разрабатывать приложения, используя драйвер Ruby для SQL Server.    
  
Обратите внимание на то, что драйвер Ruby использует протокол потока табличных данных, которое включено по умолчанию в SQL Server и базы данных SQL Azure.  Дополнительная настройка не требуется.  
  
  
## <a name="windows"></a>Windows  
  
1.  **Скачайте установщик Ruby**  
Если компьютер не является Ruby установите ее. Для новых пользователей ruby мы рекомендуем использовать Ruby 2.2.X установщиков. Они предоставляют стабильный языка и обширный список пакетов (жемчужины), совместимых и обновленный. Go [страницу загрузки Ruby](https://rubyinstaller.org/downloads/) и загрузите установщик соответствующие 2.1.x. Для примера, при работе в 64-разрядном компьютере, скачайте установщик Ruby 2.1.6 (x 64).   
  
2.  **Установите Ruby**  
Скачав установщик, сделайте следующее:  
A. Дважды щелкните файл, чтобы запустить установщик.  
Б. Выберите язык и примите условия.  
в.  На экране параметров установки установите флажки рядом с обоих добавить Ruby исполняемых файлов .rb и .rbw файлов пути и сопоставьте ее с помощью Ruby установки.  
  
3.  **Скачайте Ruby DevKit**  
Скачать на странице RubyInstaller DevKit  
  
4.  **Установите Ruby DevKit**  
После завершения загрузки, сделайте следующее:  
A. Дважды щелкните файл. Вам нужно будет where для извлечения файлов.  
Б. Нажмите кнопку «…» и выберите «C:\DevKit». Скорее всего, потребуется сначала создать эту папку, нажав кнопку «Создать папку».  
в. Нажмите кнопку «ОК», а затем «извлечь», чтобы извлечь файлы.  
  
5. **Откройте cmd.exe**  
  
6. **Инициализируйте Ruby DevKit**  
```  
> chdir C:\DevKit  
> ruby dk.rb init  
> ruby dk.rb install  
```  
  
7.  **Установка TinyTDS gem**  
```  
> gem inst tiny_tds
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux 18.04  
  
1. **Открыть терминал**  
  
2. **Установить диспетчер версий Ruby (rvm) и необходимых компонентов**  
```  
> sudo apt-get --assume-yes update  
> command curl -sSL https://rvm.io/mpapis.asc | gpg --import -  
> curl -L https://get.rvm.io | bash -s stable  
> source ~/.rvm/scripts/rvm  
```  
   
3. **Использовать rvm Установка Ruby**  
Например установите версию 2.3.0 Ruby:  
```  
> rvm install 2.3.0  
> rvm use 2.3.0 --default  
> ruby -v  
```  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Убедитесь, что выходные данные последней команды указывает, что при использовании версии 2.3.0.  
  
4.  **Установка FreeTDS**  
```  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
```  
  
5.  **Установка TinyTDS**  
```  
> gem install tiny_tds  
```  
  
## <a name="mac"></a>Mac  
  
Обратите внимание, что Mac OS X уже предварительно установлен, Ruby, зависит от операционной системы.    
  
1.  **Открыть терминал**  
  
2. **Установка диспетчера пакетов Homebrew**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
3.  **Установка FreeTDS**  
```  
> brew install FreeTDS  
```  
  
4.  **Установка TinyTDS gem**  
```  
> gem install tiny_tds  
```
