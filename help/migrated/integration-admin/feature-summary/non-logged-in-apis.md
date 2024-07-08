---
description: 了解開發無頭介面的非登錄 API。
jcr-language: en_us
title: 非登入 API
source-git-commit: 21e2a4a5e73fcbddb64e0afec0a896b315e38688
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# 非登入 API

在本文中了解有關 Adobe Systems 學習管理器 API 的詳細信息，這些 API 為無頭或非登錄體驗提供數據。公用Search API

## 公用Search API

### 使用公共 ES 篩選数据

公共Search API 允許您獲取可與基本 搜尋 API 一起使用以篩選課程的篩選器數據。 此 API 提供可在 搜尋 API 中使用的所有篩選器。

**示例捲曲**

使用GET 方法進行以下請求。 在 &lt;Base_URL> 下面的 curl 命令中使用基本URL取代。 &lt;/Base_URL>可以在 &lt;Base_URL> 訓練資料訪問連接器上找到頁面。&lt;/Base_URL>

```
curl --location '<Base_URL>/filterableData'
```

**範例回應**

```
{
    "terms": {
        "loSkillLevels": [
            "1"
        ],
        "catalogNames": [
            "Default Catalog"
        ],
"catalogLabelIds": [
            "0000_1111"
        ],
        "loType": [
            "course"
        ],
        "availability": [
            "waitlistAvailable",
            "seatAvailable"
        ],
        "loSkillNames": [
            "General"
        ],
        "tags": [
            "course_tag"
        ],
        "authors": [
            "author_1"        
]
    },
    "range": {
        "duration": [
            "0"
        ],
        "dateCreated": [
            "2024-06-13T04:32:17.000Z"
        ],
        "price": [
            "0.0"
        ],
        "sessionEndTime": [
            "2024-06-18T20:30:00.000Z"
        ],
        "averageRating": [
            "0.0"
        ],
        "sessionStartTime": [
            "2024-06-18T19:30:00.000Z"
        ],
        "publishDate": [
            "2024-06-13T04:32:51.000Z"
        ],
        "ratingsCount": [
            "0"
        ]
    },
    "term": {}
}
```

**篩選選項**

| 選項 | 說明 |
| --- | --- |
| `loSkillLevels` | 他註冊課程所需的熟練程度。 |
| `catalogNames` | 可用目錄名稱的清單。 |
| `loType` | 可用學習物件的類型。 |
| `availability` | 授權可用性和候補名單可用性。 |
| `loSkillNames` | 添加到學習物件的技能名稱。 |
| `tags` | 與學習對象關聯的標記。 |
| `authors` | 學習物件的作者名稱 |
| `duration` | 學習對象的持續時間。 |
| `dateCreated` | 創建學習物件的日期。 |
| `sessionEndTime` | 會話結束的時間。 |
| `averageRating` | 學習物件的平均星級評定。 |
| `sessionStartTime` | 會話開始的時間。 |
| `publishDate` | 學習物件的發佈日期。 |
| `ratingsCount` | 學習對象的評分計數。 |

### Search API

公共Search API 允許您使用提供的數據獲取基本的搜尋数据。

**範例捲曲**

使用POST 方法進行以下請求。 在 &lt;Base_URL> 下面的 curl 命令中使用基本URL取代。 &lt;/Base_URL>可以在 &lt;Base_URL> 訓練資料訪問連接器上找到頁面。&lt;/Base_URL>

```
curl --location '<Base_URL>/search?size=1000' \
--header 'content-type: application/json' 

--data '{
   "query": "",
   
    "sort": {
        "name": "publishDate",
        "order": "desc"
    },
    "lang": [
        "en-US"
    ],
    "filters": {
        "terms": {
            "loType": [
                "course",
                "learningProgram",
                "certification"
            ],
            "availability": [
                "seatAvailable",
                "waitlistAvailable"
            ]
        },
        "term": {
            "enrollmentDeadlinePassed": "true"
        },
        "range": {
                "dateCreated": [
                    {
                        "gte": "2024-05-02T02:48:51.000Z"
                    }
                ],
            "sessionStartTime": [
                {
                   "gte": "2024-06-18T19:30:00.000Z"
                }
            ],
            "sessionEndTime": [
                {
                   "lte": "2024-06-20T09:30:00.000Z"     
                }
            ]
        }
    }
}'
```

**API 呼叫的範例回應**

```
{
    "results": [
        {
            "loId": "course:11332313",
            "loType": "course",
            "tags": [
                "course_tag"
            ],
            "authors": [
                "author1",
                "author2"
            ],
            "status": "Published",
            "duration": 0,
            "publishDate": "2024-06-13T04:32:51.000Z",
            "dateCreated": "2024-06-13T04:32:17.000Z",
            "name": "vc coursse to check ",
            "averageRating": 0.0,
            "ratingsCount": 0,
            "loSkillNames": [
                "General"
            ],
            "loSkillLevels": [
                "1"
            ],
            "loInstances": [
                {
                    "id": "14346696",
                    "name": "Default Instance",
                    "status": "Active",
                    "price": 0.0
                }
            ],
            "catalogInfo": [
                {
                    "id": "37779",
                    "name": "Default Catalog"
                }
            ]
        }
    ],
    "request": {
        "query": "",
        "filters": {
            "terms": {
                "loType": [
                    "course",
                    "learningProgram",
                    "certification"
                ],
                "loSkillNames": [
                    "General"
                ],
                "deliveryType": [],
                "availability": [
                    "seatAvailable",
                    "waitlistAvailable"
                ]
            },
            "term": {
                "enrollmentDeadlinePassed": "true"
            },
            "range": {
                "dateCreated": [
                    {
                        "gte": "2024-05-02T02:48:51.000Z"
                    }
                ],
                "sessionStartTime": [
                    {
                        "gte": "2024-06-18T19:30:00.000Z"
                    }
                ],
                "sessionEndTime": [
                    {
                        "lte": "2024-06-20T09:30:00.000Z"
                    }
                ]
            }
        },
        "sort": {
            "name": "publishDate",
            "order": "desc"
        },
        "lang": [
            "en-US"
        ]
    },
    "self": "<Base_URL>/search?page=0&size=1000",
    "count": 1
}
```

**Search API 上的排序選項**

您可以選擇以下排序選項以應用於結果。

| 選項 | 說明 |
| --- | --- |
| `duration` | 學習對象的持續時間。 |
| `publishDate` | 學習物件的發佈日期。 |
| `dateCreated` | 創建學習物件的日期。 |
| `name_en` | 學習物件的名稱。 |
| `averageRating` | 學習者提供的平均星級評分。 |
| `ratingsCount` | 學習對象的評分計數。 |
| `relevance(default)` | 相關數據基於搜尋關鍵字。 |

### 使用公用 搜尋 API 取得學習物件数据

通過公共 ES 學習物件 API，您可以獲取無頭介面上可用的學習物件的類型和 ID 的清單。

**示例捲曲**

使用GET 方法進行以下請求。 在 &lt;Base_URL> 下面的 curl 命令中使用基本URL取代。 &lt;/Base_URL>可以在 &lt;Base_URL> 訓練資料訪問連接器上找到頁面。&lt;/Base_URL>

```
curl --location '<Base_URL>/learningObjectIds'
```

**API 呼叫的範例回應**

```
{
    "loIds": [
        "course:1132800",
"certification:126009",
"learningProgram:104433"
    ]
}
```

## 課程摘要 API

課程摘要 API 允許您檢索有關特定課程的詳細資訊。

**示例捲曲**

使用GET 方法進行以下請求。 在 &lt;Base_URL> 下面的 curl 命令中使用基本URL取代。 &lt;/Base_URL>可以在 &lt;Base_URL> 訓練資料訪問連接器上找到頁面。 &lt;/Base_URL>&lt;Course_ID> 取代特定課程ID。&lt;/Course_ID>

```
curl --location '<Base_URL>/loSummary?loId=course%3A<Course_ID>'
```

**API 呼叫的範例回應**

```
{
    "results": [
        {
            "instanceId": "14336686",
            "courseId": "11312313",
            "accountId": "44355",
            "seatConsumed": 1,
            "seatLimit": 1,
            "waitlistLimit":1,
            "waitlistCount": 1,
            "seatAvailable": false,
            "waitlistAvailable": false
        }
    ],
    "count": 1
}
```

>[!NOTE]
>
>如果課程有多個實例，則您將獲得所有實例的詳細資訊。

## CDN JSON API 課程詳細資訊

CDN JSON API 允許您檢索有關特定課程的完整課程資訊。

**課程捲曲示例**

使用GET 方法進行以下請求。 在 &lt;CDN_path> 下面的 curl 命令中使用基本URL取代。 &lt;/CDN_path>可以在 &lt;CDN_path> 訓練資料訪問連接器上找到頁面。 &lt;/CDN_path>&lt;Course_ID> 取代特定課程ID。&lt;/Course_ID>

```
curl --location '<CDN_path_URL>/course/<Course_ID>.json'
```

**用於學習路徑和認證的樣本捲曲**

```
curl --location '<CDN_path_URL>/learningProgram/<LearningProgram_ID>.json'
```

```
curl --location '<CDN_path_URL>/ certification /<Certification_ID>.json'
```

**API 呼叫的範例回應**

```
{
    "data": {
        "id": "course:11342313",
        "type": "learningObject",
        "attributes": {
            "authorNames": [
                "author1",
                "author2"
            ],
            "dateCreated": "2024-06-13T04:32:17.000Z",
            "datePublished": "2024-06-13T04:32:51.000Z",
            "dateUpdated": "2024-06-13T04:32:51.000Z",
            "duration": 0,
            "effectiveModifiedDate": "2024-06-13T04:32:51.000Z",
            "effectivenessIndex": 0,
            "enrollmentType": "Self Enroll",
            "hasOptionalLoResources": false,
            "hasPreview": false,
            "isExternal": false,
            "isMqaEnabled": false,
            "isPrerequisiteEnforced": false,
            "isSubLoOrderEnforced": false,
            "loResourceCompletionCount": 1,
            "loType": "course",
            "moduleResetEnabled": false,
            "state": "Published",
            "tags": [
                "course_tag"
            ],
            "unenrollmentAllowed": true,
            "localizedMetadata": [
                {
                    "description": "",
                    "locale": "en-US",
                    "name": "vc coursse to check "
                }
            ],
            "rating": {
                "averageRating": 0,
                "ratingsCount": 0
            }
        },
        "relationships": {
            "authors": {
                "data": [
                    {
                        "id": "13138897",
                        "type": "user"
                    }
                ]
            },
            "instances": {
                "data": [
                    {
                        "id": "course:11332313_14336696",
                        "type": "learningObjectInstance"
                    }
                ]
            },
            "skills": {
                "data": [
                    {
                        "id": "course:11332313_237719",
                        "type": "learningObjectSkill"
                    }
                ]
            }
        }
    },
    "included": [
        {
            "id": "237719",
            "type": "skill",
            "attributes": {
                "name": "General",
                "state": "Active"
            },
            "relationships": {
                "levels": {
                    "data": [
                        {
                            "id": "237719_1",
                            "type": "skillLevel"
                        }
                    ]
                }
            }
        },
        {
            "id": "course:11312313",
            "type": "learningObject",
            "attributes": {
                "authorNames": [
                    "m 41",
                    "rae"
                ],
                "dateCreated": "2024-06-13T04:32:17.000Z",
                "datePublished": "2024-06-13T04:32:51.000Z",
                "dateUpdated": "2024-06-13T04:32:51.000Z",
                "duration": 0,
                "effectiveModifiedDate": "2024-06-13T04:32:51.000Z",
                "effectivenessIndex": 0,
                "enrollmentType": "Self Enroll",
                "hasOptionalLoResources": false,
                "hasPreview": false,
                "isExternal": false,
                "isMqaEnabled": false,
                "isPrerequisiteEnforced": false,
                "isSubLoOrderEnforced": false,
                "loResourceCompletionCount": 1,
                "loType": "course",
                "moduleResetEnabled": false,
                "state": "Published",
                "tags": [
                    "course_tag"
                ],
                "unenrollmentAllowed": true,
                "localizedMetadata": [
                    {
                        "description": "",
                        "locale": "en-US",
                        "name": "course name "
                    }
                ],
                "rating": {
                    "averageRating": 0,
                    "ratingsCount": 0
                }
            },
            "relationships": {
                "authors": {
                    "data": [
                        {
                            "id": "13128897",
                            "type": "user"
                        }
                    ]
                },
                "instances": {
                    "data": [
                        {
                            "id": "course:11312313_14336696",
                            "type": "learningObjectInstance"
                        }
                    ]
                },
                "skills": {
                    "data": [
                        {
                            "id": "course:11312313_237719",
                            "type": "learningObjectSkill"
                        }
                    ]
                }
            }
        },
        {
            "id": "course:11312313_14336696_12034506_0",
            "type": "learningObjectResource",
            "attributes": {
                "externalReporting": false,
                "isExpiredSubmission": false,
                "loResourceType": "Content",
                "multipleAttemptEnabled": false,
                "previewEnabled": false,
                "resourceType": "Virtual Classroom",
                "submissionEnabled": false,
                "localizedMetadata": [
                    {
                        "description": "",
                        "locale": "en-US",
                        "name": "vc session"
                    }
                ]
            },
            "relationships": {
                "learningObject": {
                    "data": {
                        "id": "course:11312313",
                        "type": "learningObject"
                    }
                },
                "resources": {
                    "data": [
                        {
                            "id": "course:11312313_14336696_12034506_0_resource",
                            "type": "resource"
                        }
                    ]
                }
            }
        },
        {
            "id": "course:11312313_237719",
            "type": "learningObjectSkill",
            "attributes": {
                "credits": 1,
                "learningObjectId": "course:11312313"
            },
            "relationships": {
                "skillLevel": {
                    "data": {
                        "id": "237719_1",
                        "type": "skillLevel"
                    }
                }
            }
        },
        {
            "id": "13128897",
            "type": "user",
            "attributes": {
                "avatarUrl": "https://abccontents.adobe.com/public/images/default_user_avatar.svg",
                "binUserId": "1f8c01aa-7f58-42e9-bc40-11537eb6498d",
                "email": "manjusha+41re@adobetest.com",
                "enrollOnClick": false,
                "gamificationEnabled": true,
                "lastLoginDate": "2024-06-13T04:23:45.000Z",
                "name": "m 41",
                "pointsEarned": 0,
                "pointsRedeemed": 0,
                "preferredResolution": "AUTO",
                "profile": "admin",
                "roles": [
                    "Learner",
                    "Admin",
                    "Author",
                    "Instructor",
                    "Integration Admin"
                ],
                "state": "ACTIVE",
                "userType": "Internal"
            },
            "relationships": {
                "account": {
                    "data": {
                        "id": "44355",
                        "type": "account"
                    }
                }
            }
        },
        {
            "id": "course:11312313_14336696_12034506_0_resource",
            "type": "resource",
            "attributes": {
                "avatarUrls": [
                    "https://abccontents.adobe.com/public/images/default_user_avatar.svg"
                ],
                "completionDeadline": "2024-06-18T20:30:00.000Z",
                "contentType": "Virtual Classroom",
                "dateStart": "2024-06-18T19:30:00.000Z",
                "desiredDuration": 3600,
                "hasQuiz": false,
                "hasToc": false,
                "instructorNames": [
                    "instructor1"
                ],
                "isDefault": true,
                "locale": "en-US",
                "location": "http://google.com",
                "name": "vc session",
                "onlyQuiz": false,
                "reportingType": "NONE"
            }
        },
        {
            "id": "course:11312313_14336696",
            "type": "learningObjectInstance",
            "attributes": {
                "dateCreated": "2024-06-13T04:32:18.000Z",
                "isDefault": true,
                "isFlexible": false,
                "state": "Active",
                "localizedMetadata": [
                    {
                        "locale": "en-US",
                        "name": "Default Instance"
                    }
                ],
                "seatConsumed": 0,
                "waitlistCount": 0
            },
            "relationships": {
                "learningObject": {
                    "data": {
                        "id": "course:11312313",
                        "type": "learningObject"
                    }
                },
                "loResources": {
                    "data": [
                        {
                            "id": "course:11312313_14336696_12034506_0",
                            "type": "learningObjectResource"
                        }
                    ]
                }
            }
        },
        {
            "id": "237719_1",
            "type": "skillLevel",
            "attributes": {
                "level": "1",
                "maxCredits": 1,
                "name": "Level 1"
            },
            "relationships": {
                "skill": {
                    "data": {
                        "id": "237719",
                        "type": "skill"
                    }
                }
            }
        }
    ]
}
```
