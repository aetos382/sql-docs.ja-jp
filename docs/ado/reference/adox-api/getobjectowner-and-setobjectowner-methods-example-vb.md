---
title: GetObjectOwner と SetObjectOwner メソッドの例 (VB) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- SetObjectOwner method [ADOX], Visual Basic example
- GetObjectOwner method [ADOX], Visual Basic example
ms.assetid: e44ec3d4-42ae-447d-aaed-bdea53cb0cca
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c9599d5b1130b5e19a3c42614ae49df3183918e2
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35285951"
---
# <a name="getobjectowner-and-setobjectowner-methods-example-vb"></a>GetObjectOwner と SetObjectOwner メソッドの例 (VB)
この例で、 [GetObjectOwner](../../../ado/reference/adox-api/getobjectowner-method-adox.md)と[SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md)メソッドです。 このコードを想定して、グループのアカウンティング (を参照してください、[グループとユーザーの追加、ChangePassword メソッドの例 (VB)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)をシステムにこのグループを追加する方法を参照してください)。 Categories テーブルの所有者は、アカウンティングに設定されます。  
  
```  
' BeginOwnersVB  
Sub OwnersX()  
  
    Dim tblLoop As New ADOX.Table  
    Dim cat As New ADOX.Catalog  
    Dim strOwner As String  
  
    ' Open the Catalog.  
    cat.ActiveConnection = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=c:\Program Files\" & _  
        "Microsoft Office\Office\Samples\Northwind.mdb;" & _  
        "jet oledb:system database=" & _  
        "c:\Program Files\Microsoft Office\Office\system.mdw"  
  
    ' Print the original owner of Categories  
    strOwner = cat.GetObjectOwner("Categories", adPermObjTable)  
    Debug.Print "Owner of Categories: " & strOwner  
  
    ' Set the owner of Categories to Accounting  
    cat.SetObjectOwner "Categories", adPermObjTable, "Accounting"  
  
    ' List the owners of all tables and columns in the catalog.  
    For Each tblLoop In cat.Tables  
        Debug.Print "Table: " & tblLoop.Name  
        Debug.Print "   Owner: " & _  
            cat.GetObjectOwner(tblLoop.Name, adPermObjTable)  
    Next tblLoop  
  
    ' Restore the original owner of Categories  
    cat.SetObjectOwner "Categories", adPermObjTable, strOwner  
  
End Sub  
' EndOwnersVB  
```  
  
## <a name="see-also"></a>参照  
 [カタログ オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [GetObjectOwner メソッド (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)   
 [SetObjectOwner メソッド](../../../ado/reference/adox-api/setobjectowner-method.md)
