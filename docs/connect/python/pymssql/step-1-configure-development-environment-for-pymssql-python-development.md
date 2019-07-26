---
title: Шаг 1. Настройка среды разработки pymssql Python | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6d392a5e-b08e-4b35-9e99-61260888fc41
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5bf2942b79cf7e72efbb36a53019de8208cd3b8e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67935825"
---
# <a name="step-1-configure-development-environment-for-pymssql-python-development"></a>Шаг 1. Настройка среды разработки для разработки на Python в pymssql
Чтобы разработать приложение с помощью драйвера Python для SQL Server, необходимо настроить среду разработки с учетом необходимых условий.    
  
Обратите внимание, что драйверы Python SQL используют протокол TDS, который по умолчанию включен в SQL Server и базу данных SQL Azure.  Дополнительная настройка не требуется.  
  
## <a name="windows"></a>Windows  
  
1. **Установка среды выполнения Python и диспетчера пакетов PIP**  
A. Перейдите по адресу [Python.org](https://www.python.org/downloads/)  
Б. Щелкните соответствующую ссылку MSI установщика Windows.   
в. После скачивания запустите MSI, чтобы установить среду выполнения Python.  
  
2. **Скачайте модуль pymssql** [отсюда](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pymssql)  
  
    Убедитесь, что выбран правильный файл WHL.  Например, если на компьютере 64 бит используется Python 2,7, выберите: пимсскл-,-cp27-None-win_amd64. WHL. После загрузки WHL-файла поместите его в папку C:/Python27.  
      
3. **Открыть CMD. exe**  
  
4. **Установка модуля pymssql**     
    Например, при использовании Python 2,7 на компьютере 64 бит:  
```  
> cd c:\Python27  
> pip install pymssql‑2.1.1‑cp27‑none‑win_amd64.whl  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Установка среды выполнения Python и диспетчера пакетов PIP**  Python предварительно установлен в большинстве дистрибутивов Ubuntu.  Если на компьютере не установлено приложение Python, можно скачать исходный tarball из [Python.org](https://www.python.org/downloads/) и выполнить сборку локально. также можно использовать диспетчер пакетов:  
```  
> sudo apt-get install python   
```  
  
2.  **Открыть терминал**  
  
3.  **Установка модуля и зависимостей pymssql**  
```  
> sudo apt-get --assume-yes update  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
> sudo apt-get --assume-yes install python-dev python-pip  
> sudo pip install pymssql  
```  
  
## <a name="mac"></a>Mac  
  
1. **Установка среды выполнения Python и диспетчера пакетов PIP**  
A. Перейдите по адресу [Python.org](https://www.python.org/downloads/)  
Б. Щелкните ссылку на соответствующий пакет установщика Mac.   
в. После скачивания запустите пакет pkg, чтобы установить среду выполнения Python.  
  
2.  **Открыть терминал**  
  
3. **Установка диспетчера пакетов Homebrew**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
4.  **Установка модуля FreeTDS**  
```  
> brew install FreeTDS  
```  
  
5.  **Установка модуля pymssql**  
```  
> sudo -H pip install pymssql  
```
