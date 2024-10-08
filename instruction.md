

https://github.com/DaddyCherry/ai-102

---

python -m venv myenv
. myenv/bin/activate 

pip install python-dotenv
pip install azure-mgmt-compute
pip install azure-mgmt-storage
pip install azure-mgmt-resource
pip install azure-keyvault-secrets
pip install azure-storage-blob


----
# 1. Azure AI サービスの使用を開始する

    pip install azure-ai-textanalytics

    python ./mslearn-ai-services/Labfiles/01-use-azure-ai-services/Python/sdk-client/sdk-client.py         

    Enter some text ("quit" to stop)
    hello
    Language: English

    Enter some text ("quit" to stop)
    ソフトウェア会社を経営しています。
    Language: Japanese


---
# 2. Azure AI Vision を使用して画像を分析する

    pip install pillow
    pip install matplotlib
    pip install namespaces
    pip install azure-ai-vision-imageanalysis

    python ./mslearn-ai-vision/Labfiles/01-analyze-images/Python/image-analysis/image-analysis.py

    # 全体の流れ
        - 環境変数からAzureのエンドポイントとキーを読み込む。
        - 画像を読み込み、Azure AI Visionを使って解析（キャプション生成、オブジェクト検出など）を実行する。
        - 背景除去を行い、結果を保存する。

    # 元イメージファイル場所
    open ./mslearn-ai-vision/Labfiles/01-analyze-images/Python/image-analysis/images

    # 出力イメージファイル場所
    open .

    # 出力例

        Analyzing image...

        Caption:
        Caption: 'a man walking a dog on a leash on a street' (confidence: 82.07%)

        Dense Captions:
        Caption: 'a man walking a dog on a leash on a street' (confidence: 82.07%)
        Caption: 'a man walking on a street' (confidence: 69.02%)
        Caption: 'a yellow car on the street' (confidence: 78.22%)
        Caption: 'a black dog walking on the street' (confidence: 75.31%)
        Caption: 'a blurry image of a blue car' (confidence: 82.01%)
        Caption: 'a yellow taxi cab on the street' (confidence: 72.44%)

        Tags:
        Tag: 'outdoor' (confidence: 99.87%)
        Tag: 'land vehicle' (confidence: 99.02%)
        Tag: 'vehicle' (confidence: 98.89%)
        Tag: 'building' (confidence: 98.55%)
        Tag: 'road' (confidence: 95.98%)
        Tag: 'wheel' (confidence: 95.14%)
        Tag: 'street' (confidence: 94.71%)
        Tag: 'person' (confidence: 93.01%)
        Tag: 'clothing' (confidence: 91.19%)
        Tag: 'taxi' (confidence: 90.95%)
        Tag: 'car' (confidence: 84.01%)
        Tag: 'dog' (confidence: 82.68%)
        Tag: 'yellow' (confidence: 77.08%)
        Tag: 'walking' (confidence: 74.11%)
        Tag: 'city' (confidence: 64.80%)
        Tag: 'woman' (confidence: 57.53%)

        Objects in image:
        car (confidence: 72.40%)
        taxi (confidence: 77.00%)
        person (confidence: 78.10%)
        dog (confidence: 54.40%)
        Results saved in objects.jpg

        People in image:
        Results saved in people.jpg

        Removing background from image...
        Results saved in backgroundForeground.png 



---
# 3. 画像内のテキストの読み取り


    python ./mslearn-ai-vision/Labfiles/05-ocr/Python/read-text/read-text.py

    # 全体の流れ
        - 設定の読み込み: .envファイルからAzureのエンドポイントとキーを取得します。
        - 画像ファイルの選択: ユーザーに対して、Lincoln.jpgまたはNote.jpgを選択するメニューを提示し、画像ファイルを取得します。
        - テキストの抽出: 選択された画像ファイルをGetTextRead()で処理し、テキストの抽出を行います。
        - 結果の表示・保存: 抽出されたテキストとその位置情報を画像上に描画し、結果をコンソールに表示すると共に、新しい画像として保存します。

    # 元イメージファイル場所
    open ./mslearn-ai-vision/Labfiles/05-ocr/Python/read-text/images

    # 出力イメージファイル場所
    open .

    # 出力例

        1: Use Read API for image (Lincoln.jpg)
        2: Read handwriting (Note.jpg)
        Any other key to quit

        Enter a number:1

        Text:
        IN THIS TEMPLE
        Bounding Polygon: ((328, 171), (477, 169), (477, 184), (328, 186))
            Word: 'IN', Bounding Polygon: ((328, 171), (342, 171), (342, 187), (328, 187)), Confidence: 0.9930
            Word: 'THIS', Bounding Polygon: ((357, 171), (397, 170), (397, 185), (357, 186)), Confidence: 0.9910
            Word: 'TEMPLE', Bounding Polygon: ((407, 170), (474, 170), (474, 184), (407, 185)), Confidence: 0.9930
        AS IN THE HEARTS OF THE PEOPLE
        Bounding Polygon: ((240, 193), (564, 188), (564, 203), (240, 210))
            Word: 'AS', Bounding Polygon: ((241, 194), (262, 194), (262, 210), (241, 211)), Confidence: 0.9950
            Word: 'IN', Bounding Polygon: ((270, 193), (284, 193), (284, 210), (270, 210)), Confidence: 0.9980
            Word: 'THE', Bounding Polygon: ((298, 193), (332, 192), (332, 208), (298, 209)), Confidence: 0.9930
            Word: 'HEARTS', Bounding Polygon: ((340, 192), (410, 191), (410, 207), (340, 208)), Confidence: 0.9940
            Word: 'OF', Bounding Polygon: ((420, 190), (444, 190), (444, 206), (420, 206)), Confidence: 0.9930
            Word: 'THE', Bounding Polygon: ((452, 190), (487, 189), (487, 205), (452, 206)), Confidence: 0.9930
            Word: 'PEOPLE', Bounding Polygon: ((495, 189), (562, 188), (562, 204), (495, 205)), Confidence: 0.9960
        FOR WHOM HE SAVED THE UNION
        Bounding Polygon: ((237, 214), (568, 208), (569, 224), (237, 231))
            Word: 'FOR', Bounding Polygon: ((238, 214), (271, 213), (271, 231), (237, 231)), Confidence: 0.9950
            Word: 'WHOM', Bounding Polygon: ((281, 213), (339, 212), (339, 229), (281, 230)), Confidence: 0.9880
            Word: 'HE', Bounding Polygon: ((355, 212), (378, 212), (378, 228), (354, 229)), Confidence: 0.9980
            Word: 'SAVED', Bounding Polygon: ((388, 212), (441, 211), (440, 227), (388, 228)), Confidence: 0.9940
            Word: 'THE', Bounding Polygon: ((455, 211), (491, 210), (490, 226), (455, 227)), Confidence: 0.9930
            Word: 'UNION', Bounding Polygon: ((501, 210), (560, 209), (559, 225), (500, 226)), Confidence: 0.9970
        THE MEMORY OF ABRAHAM LINCOLN
        Bounding Polygon: ((226, 235), (575, 229), (576, 245), (226, 252))
            Word: 'THE', Bounding Polygon: ((228, 235), (260, 235), (260, 252), (228, 252)), Confidence: 0.9980
            Word: 'MEMORY', Bounding Polygon: ((268, 235), (349, 234), (349, 250), (268, 251)), Confidence: 0.9960
            Word: 'OF', Bounding Polygon: ((358, 234), (382, 234), (381, 250), (357, 250)), Confidence: 0.9990
            Word: 'ABRAHAM', Bounding Polygon: ((389, 233), (473, 232), (472, 248), (389, 249)), Confidence: 0.9960
            Word: 'LINCOLN', Bounding Polygon: ((488, 231), (570, 229), (570, 245), (487, 247)), Confidence: 0.9940
        IS ENSHRINED FOREVER
        Bounding Polygon: ((288, 255), (515, 253), (516, 268), (288, 271))
            Word: 'IS', Bounding Polygon: ((288, 256), (302, 256), (302, 272), (288, 272)), Confidence: 0.9960
            Word: 'ENSHRINED', Bounding Polygon: ((311, 256), (416, 255), (417, 270), (311, 272)), Confidence: 0.9930
            Word: 'FOREVER', Bounding Polygon: ((431, 255), (510, 253), (511, 268), (431, 270)), Confidence: 0.9950

        Results saved in text.jpg

        1: Use Read API for image (Lincoln.jpg)
        2: Read handwriting (Note.jpg)
        Any other key to quit

        Enter a number:2

        Text:
        Shopping List
        Bounding Polygon: ((231, 141), (693, 147), (691, 245), (230, 240))
            Word: 'Shopping', Bounding Polygon: ((240, 141), (535, 149), (531, 245), (234, 234)), Confidence: 0.9630
            Word: 'List', Bounding Polygon: ((554, 149), (689, 147), (686, 244), (550, 245)), Confidence: 0.8300
        Non- Fat milk
        Bounding Polygon: ((149, 302), (633, 297), (633, 374), (150, 378))
            Word: 'Non-', Bounding Polygon: ((150, 303), (309, 301), (310, 378), (153, 378)), Confidence: 0.5770
            Word: 'Fat', Bounding Polygon: ((324, 301), (438, 300), (437, 378), (325, 378)), Confidence: 0.8420
            Word: 'milk', Bounding Polygon: ((476, 299), (620, 298), (617, 374), (475, 377)), Confidence: 0.9940
        Bread
        Bounding Polygon: ((138, 400), (382, 399), (383, 472), (138, 474))
            Word: 'Bread', Bounding Polygon: ((152, 400), (366, 400), (368, 471), (151, 475)), Confidence: 0.9950
        Eggs
        Bounding Polygon: ((146, 517), (351, 526), (348, 605), (146, 609))
            Word: 'Eggs', Bounding Polygon: ((149, 517), (342, 519), (341, 610), (148, 609)), Confidence: 0.9920

        Results saved in text.jpg



---
# 4. Azure AI Vision カスタム モデルを使用して画像を分類する

    Storage Account

        fruitというコンテナを作成

        サンプルのCOCOファイルのurlを書き換える
        "absolute_url": "https://<storageAccount>.blob.core.windows.net/fruit/IMG_20200229_164823.jpg",

        サンプルファイルをBlobストレージにアップロード
        https://portal.azure.com/#view/Microsoft_Azure_Storage/ContainerMenuBlade/~/overview/storageAccountId/%2Fsubscriptions%2F76acff29-d96c-4618-b187-4ab5f53172f0%2FresourceGroups%2Fdelivery%2Fproviders%2FMicrosoft.Storage%2FstorageAccounts%2Fdemostr241008/path/fruits/etag/%220x8DCE75C4A7695D1%22/defaultEncryptionScope/%24account-encryption-key/denyEncryptionScopeOverride~/false/defaultId//publicAccessVal/Blob

    Vision Studio

        https://portal.vision.cognitive.azure.com/

        Datasetを追加
        https://portal.vision.cognitive.azure.com/resource/r/c003bbfc9f6249d98fdab797f9845618/subscriptions/76acff29-d96c-4618-b187-4ab5f53172f0/datasets

        COCOファイルをストレージアカウントからインポート
        training_labels.json
    
        新しいモデルのトレーニング
        ※ トレーニングには数時間かかることがあります。検証時には25分程度で終了。

        Try it outでテスト



---
# 5. テキストの分析

    pip install azure-ai-textanalytics

    python ./mslearn-ai-language/Labfiles/01-analyze-text/Python/text-analysis/text-analysis.py

    # 全体の流れ
        - .envファイルからAzureのサービスエンドポイントとキーを取得。
        - TextAnalyticsClientを使ってテキスト解析を行うクライアントを初期化。
        - reviewsフォルダ内の各テキストファイルを読み込み、言語、感情、キーフレーズ、エンティティなどの解析を順に実行。
        - 解析結果をコンソールに表示。

    # 出力例

        -------------
        review3.txt

        Good location and helpful staff, but on a busy road.
        The Lombard Hotel, San Francisco, USA
        8/16/2018
        We stayed here in August after reading reviews. We were very pleased with location, just behind Chestnut Street, a cosmopolitan and trendy area with plenty of restaurants to choose from. The
        Marina district was lovely to wander through, very interesting houses. Make sure to walk to the San Francisco Museum of Fine Arts and the Marina to get a good view of Golden Gate bridge and the city. On a
        Marina district was lovely to wander through, very interesting houses. Make sure to walk to the San Francisco Museum of Fine Arts and the Marina to get a good view of Golden Gate bridge and the city. On a bus route and easy to get into centre. Rooms were clean with plenty of room and staff were friendly and helpful. The only down side was the noise from Lombard Street so ask to have a room furthest away f
        Marina district was lovely to wander through, very interesting houses. Make sure to walk to the San Francisco Museum of Fine Arts and the Marina to get a good view of Golden Gate bridge and the city. On a bus route and easy to get into centre. Rooms were clean with plenty of room and staff were friendly and helpful. The only down side was the noise from Lombard Street so ask to have a room furthest away from traffic noise.

        Language: English

        Sentiment: mixed

        Key Phrases:
                Golden Gate bridge
                The Lombard Hotel
                The Marina district
                San Francisco Museum
                Lombard Street
                busy road
                Chestnut Street
                trendy area
                interesting houses
                Fine Arts
                good view
                bus route
                down side
                Good location
                helpful staff
                traffic noise
                USA
                We
                August
                reviews
                cosmopolitan
                plenty
                restaurants
                city
                centre
                Rooms

        Entities
                staff (PersonType)
                road (Location)
                Lombard Hotel (Location)
                San Francisco (Location)
                USA (Location)
                8/16/2018 (DateTime)
                August (DateTime)
                Chestnut Street (Location)
                restaurants (Location)
                Marina district (Location)
                houses (Location)
                San Francisco Museum of Fine Arts (Location)
                Marina (Location)
                Golden Gate bridge (Location)
                city (Location)
                centre (Location)
                Rooms (Location)
                staff (PersonType)
                Lombard Street (Address)
                room (Location)

        Links
                Lombardy (https://en.wikipedia.org/wiki/Lombardy)
                Hotel (https://en.wikipedia.org/wiki/Hotel)
                San Francisco (https://en.wikipedia.org/wiki/San_Francisco)
                Chestnut Street (Philadelphia) (https://en.wikipedia.org/wiki/Chestnut_Street_(Philadelphia))
                Marina District, San Francisco (https://en.wikipedia.org/wiki/Marina_District,_San_Francisco)
                Museum of Fine Arts, Boston (https://en.wikipedia.org/wiki/Museum_of_Fine_Arts,_Boston)
                Golden Gate Bridge (https://en.wikipedia.org/wiki/Golden_Gate_Bridge)
                Room (https://en.wikipedia.org/wiki/Room)
                Lombard Street (San Francisco) (https://en.wikipedia.org/wiki/Lombard_Street_(San_Francisco))

        -------------
        review2.txt

        Tired hotel with poor service
        The Royal Hotel, London, United Kingdom
        5/6/2018
        This is a old hotel (has been around since 1950's) and the room furnishings are average - becoming a bit old now and require changing. The internet didn't work and had to come to one of their office rooms
        This is a old hotel (has been around since 1950's) and the room furnishings are average - becoming a bit old now and require changing. The internet didn't work and had to come to one of their office rooms to check in for my flight home. The website says it's close to the British Museum, but it's too far to walk.

        Language: English

        Sentiment: negative

        Key Phrases:
                The Royal Hotel
                Tired hotel
                old hotel
                poor service
                United Kingdom
                room furnishings
                office rooms
                flight home
                British Museum
                London
                changing
                internet
                website
                1950

        Entities
                hotel (Location)
                Hotel (Location)
                London (Location)
                United Kingdom (Location)
                5/6/2018 (DateTime)
                hotel (Location)
                since 1950 (DateTime)
                room (Location)
                now (DateTime)
                internet (Skill)
                one (Quantity)
                office rooms (Location)
                flight (Event)
                home (Location)
                British Museum (Location)

        Links
                The Royal Hotel (https://en.wikipedia.org/wiki/The_Royal_Hotel)
                London (https://en.wikipedia.org/wiki/London)
                British Museum (https://en.wikipedia.org/wiki/British_Museum)

        -------------
        review1.txt

        Good Hotel and staff
        The Royal Hotel, London, UK
        3/2/2018
        Clean rooms, good service, great location near Buckingham Palace and Westminster Abbey, and so on. We thoroughly enjoyed our stay. The courtyard is very peaceful and we went to a restaurant which is part 
        Clean rooms, good service, great location near Buckingham Palace and Westminster Abbey, and so on. We thoroughly enjoyed our stay. The courtyard is very peaceful and we went to a restaurant which is part of the same group and is Indian ( West coast so plenty of fish) with a Michelin Star. We had the taster menu which was fabulous. The rooms were very well appointed with a kitchen, lounge, bedroom and enor
        Clean rooms, good service, great location near Buckingham Palace and Westminster Abbey, and so on. We thoroughly enjoyed our stay. The courtyard is very peaceful and we went to a restaurant which is part of the same group and is Indian ( West coast so plenty of fish) with a Michelin Star. We had the taster menu which was fabulous. The rooms were very well appointed with a kitchen, lounge, bedroom and enormous bathroom. Thoroughly recommended.

        Language: English

        Sentiment: positive

        Key Phrases:
                The Royal Hotel
                Good Hotel
                good service
                great location
                Buckingham Palace
                Westminster Abbey
                same group
                West coast
                Michelin Star
                taster menu
                enormous bathroom
                Clean rooms
                staff
                London
                UK
                stay
                courtyard
                restaurant
                part
                plenty
                fish
                kitchen
                lounge
                bedroom

        Entities
                staff (PersonType)
                Royal Hotel (Location)
                London (Location)
                UK (Location)
                3/2/2018 (DateTime)
                rooms (Location)
                Buckingham Palace (Location)
                Westminster Abbey (Location)
                stay (Event)
                courtyard (Location)
                restaurant (Location)
                Indian (Skill)
                West coast (Location)
                fish (Product)
                rooms (Location)
                kitchen (Location)
                lounge (Location)
                bedroom (Location)
                bathroom (Location)

        Links
                GOOD Music (https://en.wikipedia.org/wiki/GOOD_Music)
                Hotel (https://en.wikipedia.org/wiki/Hotel)
                The Royal Hotel (https://en.wikipedia.org/wiki/The_Royal_Hotel)
                London (https://en.wikipedia.org/wiki/London)
                Buckingham Palace (https://en.wikipedia.org/wiki/Buckingham_Palace)
                Westminster Abbey (https://en.wikipedia.org/wiki/Westminster_Abbey)
                India (https://en.wikipedia.org/wiki/India)
                West Coast Main Line (https://en.wikipedia.org/wiki/West_Coast_Main_Line)
                Michelin Guide (https://en.wikipedia.org/wiki/Michelin_Guide)

        -------------
        review5.txt

        Un hôtel agréable
        L'Hotel Buckingham, Londres, UK
        J’adore cet hôtel. Le personnel est très amical et les chambres sont confortables.

        Language: French

        Sentiment: positive

        Key Phrases:
                hôtel agréable
                L'Hotel Buckingham
                Londres
                UK
                personnel
                chambres

        Entities
                hôtel (Location)
                Hotel Buckingham (Location)
                Londres (Location)
                UK (Location)
                hôtel (Location)
                personnel (PersonType)
                amical (Skill)
                chambres (Location)

        Links
                United Nations (https://en.wikipedia.org/wiki/United_Nations)
                L'Hôtel (https://en.wikipedia.org/wiki/L'Hôtel)
                Buckingham (https://en.wikipedia.org/wiki/Buckingham)
                London (https://en.wikipedia.org/wiki/London)
                United Kingdom (https://en.wikipedia.org/wiki/United_Kingdom)

        -------------
        review4.txt

        Very noisy and rooms are tiny
        The Lombard Hotel, San Francisco, USA
        9/5/2018
        Hotel is located on Lombard street which is a very busy SIX lane street directly off the Golden Gate Bridge. Traffic from early morning until late at night especially on weekends. Noise would not be so ba
        Hotel is located on Lombard street which is a very busy SIX lane street directly off the Golden Gate Bridge. Traffic from early morning until late at night especially on weekends. Noise would not be so bad if rooms were better insulated but they are not. Had to put cotton balls in my ears to be able to sleep--was too tired to enjoy the city the next day. Rooms are TINY. I picked the room because it had tw
        Hotel is located on Lombard street which is a very busy SIX lane street directly off the Golden Gate Bridge. Traffic from early morning until late at night especially on weekends. Noise would not be so bad if rooms were better insulated but they are not. Had to put cotton balls in my ears to be able to sleep--was too tired to enjoy the city the next day. Rooms are TINY. I picked the room because it had two queen size beds--but the room barely had space to fit them. With family of four in the room it was tight. With all that said, rooms are clean and they've made an effort to update them. The hotel is in M
        Hotel is located on Lombard street which is a very busy SIX lane street directly off the Golden Gate Bridge. Traffic from early morning until late at night especially on weekends. Noise would not be so bad if rooms were better insulated but they are not. Had to put cotton balls in my ears to be able to sleep--was too tired to enjoy the city the next day. Rooms are TINY. I picked the room because it had two queen size beds--but the room barely had space to fit them. With family of four in the room it was tight. With all that said, rooms are clean and they've made an effort to update them. The hotel is in Marina district with lots of good places to eat, within walking distance to Presidio. May be good hotel for young stay-up-late adults on a budget


        Language: English

        Sentiment: mixed

        Key Phrases:
                two queen size beds
                busy SIX lane street
                Golden Gate Bridge
                The Lombard Hotel
                Lombard street
                San Francisco
                early morning
                cotton balls
                Marina district
                good places
                walking distance
                late adults
                good hotel
                rooms
                USA
                Traffic
                night
                weekends
                Noise
                ears
                city
                TINY
                space
                family
                effort
                lots
                Presidio
                young
                budget

        Entities
                rooms (Location)
                Lombard Hotel (Location)
                San Francisco (Location)
                USA (Location)
                9/5/2018 (DateTime)
                Hotel (Location)
                Lombard street (Address)
                SIX (Quantity)
                Golden Gate Bridge (Location)
                Traffic (Skill)
                early morning until late at night (DateTime)
                weekends (DateTime)
                rooms (Location)
                cotton balls (Product)
                the next day (DateTime)
                Rooms (Location)
                room (Location)
                two (Quantity)
                beds (Product)
                room (Location)
                four (Quantity)
                room (Location)
                rooms (Location)
                hotel (Location)
                Marina district (Location)
                Presidio (Location)
                adults (PersonType)

        Links
                Lombard, Illinois (https://en.wikipedia.org/wiki/Lombard,_Illinois)
                Hotel (https://en.wikipedia.org/wiki/Hotel)
                San Francisco (https://en.wikipedia.org/wiki/San_Francisco)
                Lombard Street (San Francisco) (https://en.wikipedia.org/wiki/Lombard_Street_(San_Francisco))
                Golden Gate Bridge (https://en.wikipedia.org/wiki/Golden_Gate_Bridge)
                Traffic (https://en.wikipedia.org/wiki/Traffic)
                Noise rock (https://en.wikipedia.org/wiki/Noise_rock)
                Room (https://en.wikipedia.org/wiki/Room)
                Marina District, San Francisco (https://en.wikipedia.org/wiki/Marina_District,_San_Francisco)
                Presidio of San Francisco (https://en.wikipedia.org/wiki/Presidio_of_San_Francisco)
                May (https://en.wikipedia.org/wiki/May)



---
# 6. 質問応答ソリューションを作成する

---
# 7. 言語サービスで言語理解モデルを作成する

---
# 8. 音声の認識と合成

    音声サービスのキーとエンドポイントを取得し、envファイルに設定。

    pip install azure-cognitiveservices-speech
    pip install --upgrade pip setuptools wheel
    pip install playsound

    python ./mslearn-ai-language/Labfiles/07-speech/Python/speaking-clock/speaking-clock.py

        マイクで話しかけると、音声認識が実行され、テキストに変換される。
        「what time is it?」と話しかけると、時刻を音声で合成し、結果をコンソールに表示する。

    # 全体の流れ
        - 環境設定の読み込み: .envファイルからAzureの音声サービスキーとリージョンを取得。
        - 音声入力の取得: ユーザーがマイクに話しかけると、音声認識が実行され、テキストに変換されます。
        - 時刻の確認: 変換されたテキストが「what time is it?」の場合、TellTime()関数が呼び出され、現在の時刻が音声で返されます。
        - 時刻の返答: 時刻を音声で合成し、結果をコンソールに表示します。

    # 出力例
        playsound is relying on a python 2 subprocess. Please use `pip3 install PyObjC` if you want playsound to run more efficiently.
        Ready to use speech service in: japaneast
        Speak now...

        What time is it?
            Info: on_underlying_io_bytes_received: Close frame received
            Info: on_underlying_io_bytes_received: closing underlying io.
            Info: on_underlying_io_close_complete: uws_state: 6.

        TellTime
        The time is 17:16
            Info: on_underlying_io_bytes_received: Close frame received
            Info: on_underlying_io_bytes_received: closing underlying io.
            Info: on_underlying_io_close_complete: uws_state: 6.


---
# 9. アプリで Azure OpenAI API を使う

---
# 10. アプリでプロンプト エンジニアリングを利用する

---
# 11. Azure OpenAI Service を使用して検索拡張生成 (RAG) を実装する

---
# 12. Azure AI Search のカスタム スキルを作成する

---
# 13. フォームからデータを抽出する

