---
title: Шаг 1. Настройка среды pymssql
description: На шаге 1 этого руководства по началу работы предполагается установка Python, Microsoft ODBC Driver for SQL Server и pymssql в среду разработки.
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6d392a5e-b08e-4b35-9e99-61260888fc41
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d5eb4a746cf8847c8300091677fe4e07e8173707
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81634612"
---
# <a name="step-1-configure-development-environment-for-pymssql-python-development"></a>Шаг 1. Настройка среды разработки для разработки на Python в pymssql
Чтобы разработать приложение с помощью драйвера Python для SQL Server, необходимо настроить среду разработки, учитывая необходимые условия.    
  
Драйверы Python SQL используют протокол TDS, включенный по умолчанию в SQL Server и Базу данных SQL Azure.  Дополнительная настройка не требуется.  
  
## <a name="windows"></a>Windows  
  
1. **Установите среду выполнения Python и диспетчер пакетов PIP.**  
а. Перейдите на [Python.org](https://www.python.org/downloads/)  
b. Нажмите на соответствующую ссылку установщика msi Windows.   
c. После загрузки запустите msi, чтобы установить среду Python.  
  
2. **Загрузите модуль pymssql** [здесь](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pymssql)  
  
    Убедитесь, что выбран правильный файл `whl`.  Пример: Если вы используете Python 2.7 на 64-разрядном компьютере, выберите `pymssql‑2.1.1‑cp27‑none‑win_amd64.whl`. После загрузки файла `whl` разместите его в папке C:\Python27.  
      
3. **Откройте cmd.exe**  
  
4. **Установите модуль pymssql.**  
    Например, если вы используете Python 2.7 на 64-разрядном компьютере:  
```  
> cd c:\Python27  
> pip install pymssql‑2.1.1‑cp27‑none‑win_amd64.whl  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Установите среду выполнения Python и диспетчер пакетов PIP.**  Python предварительно установлен в большинстве дистрибутивов Ubuntu.  Если на вашем компьютере не установлен Python, вы можете скачать исходный архив tarball с [python.org](https://www.python.org/downloads/) и собрать его локально либо воспользоваться диспетчером пакетов:  
```  
> sudo apt-get install python   
```  
  
2.  **Откройте терминал**  
  
3.  **Установите модуль и зависимости pymssql**  
```  
> sudo apt-get --assume-yes update  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
> sudo apt-get --assume-yes install python-dev python-pip  
> sudo pip install pymssql  
```  
  
## <a name="macos"></a>macOS
  
1. **Установите среду выполнения Python и диспетчер пакетов PIP**  
а. Перейдите на [Python.org](https://www.python.org/downloads/)  
b. Щелкните ссылку на соответствующий установщик pkg macOS.   
c. После загрузки запустите pkg, чтобы установить среду Python.  
  
2.  **Откройте терминал**  
  
3. **Установите диспетчер пакетов Homebrew**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
4.  **Установите модуль FreeTDS**  
```  
> brew install FreeTDS  
```  
  
5.  **Установите модуль pymssql**  
```  
> sudo -H pip install pymssql  
```
