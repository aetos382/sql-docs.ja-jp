---
title: Roles オブジェクト (TMSL) |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 375a0f62bbf482a7c033d235836ea64b78cb2da2
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983874"
---
# <a name="roles-object-tmsl"></a>Roles オブジェクト (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  モデル権限のコレクションを指定するには、ロールを定義します。 ロールのメンバーシップは、Windows セキュリティの原則で構成されます。 特定のオブジェクトへのアクセスを制限するロールでは、フィルターを設定できます。  
  
## <a name="object-definition"></a>オブジェクトの定義  
 すべてのオブジェクトには、名前、型、説明、プロパティのコレクション、および注釈を含むプロパティの共通セットがあります。 **ロール**オブジェクトでは、次のプロパティもがあります。  
  
 modelPermission  
 データベースに対する権限のスコープを確立します。 有効な値は、none、  
                  読み取り、  
                  readRefresh、  
                  更新します。  
                  および管理者。 参照してください[ロールとアクセス許可&#40;Analysis Services&#41; ](../../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md)データベース アクセス許可についてはします。  
  
 メンバー  
 メンバーは、メンバーの名前と ID、メンバー名がエイリアスまたは、Windows セキュリティ プリンシパルのフレンドリ名、ID はセキュリティ識別子の両方で構成されます。 ロールの定義の両方を指定します。参照してください[SID コンポーネント](https://msdn.microsoft.com/library/windows/desktop/aa379597\(v=vs.85\).aspx)詳細については、識別子。  
  
 テーブル アクセス許可  
 テーブルのアクセス許可は、DAX 式を使用して定義されているアクセス許可を持つ名前付きオブジェクトです。 このプロパティは省略可能でセキュリティ フィルターを適用するために使用します。  
  
## <a name="usage"></a>使用方法  
 **ロール**オブジェクトを使用[Alter コマンド&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md)、[コマンドを作成する&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md)、 [CreateOrReplace コマンド&#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md)、および[Delete コマンド&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md)します。  
  
 A**ロール**オブジェクトは、モデルのプロパティですが、モデルとデータベース間の一対一のマッピングを指定したデータベース オブジェクトのプロパティとして指定することもできます。  
  
 作成する場合、置換、または、ロール オブジェクトを変更することは、オブジェクトの定義のすべての読み取り/書き込みプロパティを指定します。 読み取り/書き込みプロパティの省略は、削除であると見なされます。  
  
## <a name="full-syntax"></a>完全な構文  
 モデルのロール オブジェクトのスキーマ表現を以下に示します。  
  
```  
"roles": {  
          "type": "array",  
          "items": {  
            "description": "ModelRole object of Tabular Object Model (TOM)",  
            "type": "object",  
            "properties": {  
              "name": {  
                "type": "string"  
              },  
              "description": {  
                "anyOf": [  
                  {  
                    "type": "string"  
                  },  
                  {  
                    "type": "array",  
                    "items": {  
                      "type": "string"  
                    }  
                  }  
                ]  
              },  
              "modelPermission": {  
                "enum": [  
                  "none",  
                  "read",  
                  "readRefresh",  
                  "refresh",  
                  "administrator"  
                ]  
              },  
              "annotations": {  
                "type": "array",  
                "items": {  
                  "description": "Annotation object of Tabular Object Model (TOM)",  
                  "type": "object",  
                  "properties": {  
                    "name": {  
                      "type": "string"  
                    },  
                    "value": {  
                      "anyOf": [  
                        {  
                          "type": "string"  
                        },  
                        {  
                          "type": "array",  
                          "items": {  
                            "type": "string"  
                          }  
                        }  
                      ]  
                    }  
                  },  
                  "additionalProperties": false  
                }  
              },  
              "members": {  
                "type": "array",  
                "items": {  
                  "anyOf": [  
                    {  
                      "description": "WindowsModelRoleMember object of Tabular Object Model (TOM)",  
                      "type": "object",  
                      "properties": {  
                        "memberName": {  
                          "type": "string"  
                        },  
                        "memberId": {  
                          "type": "string"  
                        },  
                        "annotations": {  
                          "type": "array",  
                          "items": {  
                            "description": "Annotation object of Tabular Object Model (TOM)",  
                            "type": "object",  
                            "properties": {  
                              "name": {  
                                "type": "string"  
                              },  
                              "value": {  
                                "anyOf": [  
                                  {  
                                    "type": "string"  
                                  },  
                                  {  
                                    "type": "array",  
                                    "items": {  
                                      "type": "string"  
                                    }  
                                  }  
                                ]  
                              }  
                            },  
                            "additionalProperties": false  
                          }  
                        }  
                      },  
                      "additionalProperties": false  
                    },  
                    {  
                      "description": "ExternalModelRoleMember object of Tabular Object Model (TOM)",  
                      "type": "object",  
                      "properties": {  
                        "memberName": {  
                          "type": "string"  
                        },  
                        "memberId": {  
                          "type": "string"  
                        },  
                        "identityProvider": {  
                          "type": "string"  
                        },  
                        "memberType": {  
                          "enum": [  
                            "auto",  
                            "user",  
                            "group"  
                          ]  
                        },  
                        "annotations": {  
                          "type": "array",  
                          "items": {  
                            "description": "Annotation object of Tabular Object Model (TOM)",  
                            "type": "object",  
                            "properties": {  
                              "name": {  
                                "type": "string"  
                              },  
                              "value": {  
                                "anyOf": [  
                                  {  
                                    "type": "string"  
                                  },  
                                  {  
                                    "type": "array",  
                                    "items": {  
                                      "type": "string"  
                                    }  
                                  }  
                                ]  
                              }  
                            },  
                            "additionalProperties": false  
                          }  
                        }  
                      },  
                      "additionalProperties": false  
                    }  
                  ]  
                }  
              },  
              "tablePermissions": {  
                "type": "array",  
                "items": {  
                  "description": "TablePermission object of Tabular Object Model (TOM)",  
                  "type": "object",  
                  "properties": {  
                    "name": {  
                      "type": "string"  
                    },  
                    "filterExpression": {  
                      "anyOf": [  
                        {  
                          "type": "string"  
                        },  
                        {  
                          "type": "array",  
                          "items": {  
                            "type": "string"  
                          }  
                        }  
                      ]  
                    },  
                    "annotations": {  
                      "type": "array",  
                      "items": {  
                        "description": "Annotation object of Tabular Object Model (TOM)",  
                        "type": "object",  
                        "properties": {  
                          "name": {  
                            "type": "string"  
                          },  
                          "value": {  
                            "anyOf": [  
                              {  
                                "type": "string"  
                              },  
                              {  
                                "type": "array",  
                                "items": {  
                                  "type": "string"  
                                }  
                              }  
                            ]  
                          }  
                        },  
                        "additionalProperties": false  
                      }  
                    }  
                  },  
                  "additionalProperties": false  
                }  
              }  
            },  
            "additionalProperties": false  
          }  
        }  
```  
  
## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [ロールと権限 (Analysis Services)](../../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md)  
  
  
