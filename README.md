# TWITTER-Tweet-Parser

Twitter Tweet Parser is a JAVA application that allows you to serialize and de-serialize Twitter messages. These messages, called **Tweet**, are formalized in JSON format and their JSON description is made up of several elements and many attributes

Serialization means to convert an object into a JSON string , and deserialization is its inverse operation (convert a JSON string into an object)

Tweets are the basic atomic building block of all things Twitter. Tweets are also known as “status updates.” The Tweet object has a long list of ‘root-level’ attributes, including fundamental attributes such as **id**, **created_at**, and **text**. Tweet objects are also the ‘parent’ object to several child objects. Tweet child objects include **user**, **entities**, and **extended_entities**. Tweets that are geo-tagged will have a place child object.

-----------------------------
## Table of Contents

+ [Tweet JSON Schema](#Tweet-JSON-Schema)
+ [Tweet *full* sample](#Tweet-full-sample)

-----------------------------

### Tweet-JSON-Schema

<big><pre>
root
 |-- [created_at](#created_at): **string** (nullable = ***false***)
 |-- [id](#id): **long** (nullable = ***false***)
 |-- [id_str](#id_str): **string** (nullable = ***false***)
 |-- [text](#text): **string** (nullable = ***false***)
 |-- [source](#source): **string** (nullable = ***false***)
 |-- [truncated](#truncated): **boolean** (nullable = ***false***)
 |-- [in_reply_to_status_id](#in_reply_to_status_id): **long** (nullable = ***true***)
 |-- [in_reply_to_status_id_str](#in_reply_to_status_id_str): **string** (nullable = ***true***)
 |-- [in_reply_to_user_id](#in_reply_to_user_id): **long** (nullable = ***true***)
 |-- [in_reply_to_user_id_str](#in_reply_to_user_id_str): **string** (nullable = ***true***)
 |-- [in_reply_to_screen_name](#in_reply_to_screen_name): **string** (nullable = ***true***)
 |-- [user](#user): **struct** (nullable = ***false***)
 |    |-- [id](#user-id): **long** (nullable = ***false***)
 |    |-- [id_str](#user-id_str): **string** (nullable = ***false***)
 |    |-- [name](#user-name): **string** (nullable = ***false***)
 |    |-- [screen_name](#user-screen_name): **string** (nullable = ***false***)
 |    |-- [location](#user-location): **string** (nullable = ***true***)
 |    |-- [derived](#user-derived): **struct** (nullable = ***false***)
 |    |    |-- [locations](#user-derived-locations): **array** (nullable = ***false***)
 |    |    |    |-- element: **struct** (containsNull = ***false***)
 |    |    |    |    |-- [country](#user-derived-locations-country): **string** (nullable = ***false***)
 |    |    |    |    |-- [country_code](#user-derived-locations-country_code): **string** (nullable = ***false***)
 |    |    |    |    |-- [locality](#user-derived-locations-locality): **string** (nullable = ***false***)
 |    |    |    |    |-- [region](#user-derived-locations-region): **string** (nullable = ***false***)
 |    |    |    |    |-- [sub_region](#user-derived-locations-sub_region): **string** (nullable = ***false***)
 |    |    |    |    |-- [full_name](#user-derived-locations-full_name): **string** (nullable = ***false***)
 |    |    |    |    |-- [geo](#user-derived-locations-geo): **struct** (nullable = ***false***)
 |    |-- [url](#user-url): **string** (nullable = ***true***)
 |    |-- [description](#user-description): **string** (nullable = ***true***)
 |    |-- [protected](#user-protected): **boolean** (nullable = ***false***)
 |    |-- [verified](#user-verified): **boolean** (nullable = ***false***)
 |    |-- [followers_count](#user-followers_count): **long** (nullable = ***false***)
 |    |-- [friends_count](#user-friends_count): **long** (nullable = ***false***)
 |    |-- [listed_count](#user-listed_count): **long** (nullable = ***false***)
 |    |-- [favourites_count](#user-favourites_count): **long** (nullable = ***false***)
 |    |-- [statuses_count](#user-statuses_count): **long** (nullable = ***false***)
 |    |-- [created_at](#user-created_at): **string** (nullable = ***false***)
 |    |-- [profile_banner_url](#user-profile_banner_url): **string** (nullable = ***false***)
 |    |-- [profile_image_url_https](#user-profile_image_url_https): **string** (nullable = ***false***)
 |    |-- [default_profile](#user-default_profile): **boolean** (nullable = ***false***)
 |    |-- [default_profile_image](#user-default_profile_image): **boolean** (nullable = ***false***)
 |    |-- [withheld_in_countries](#user-withheld_in_countries): **array** (nullable = ***false***)
 |    |    |-- element: string (containsNull = false)
 |    |-- [withheld_scope](#user-withheld_scope): **string** (nullable = ***false***)
 |-- [coordinates](#coordinates): **struct** (nullable = ***true***)
 |    |-- [coordinates](#coordinates-coordinates): **array** (nullable = ***false***)
 |    |    |-- element: **double** (containsNull = ***false**)
 |    |-- [type](#coordinates-coordinates-type): **string** (nullable = ***false***)
 |-- [place](#place): **struct** (nullable = ***true***)
 |    |-- [id](#place-id): **string** (nullable = ***false***)
 |    |-- [url](#place-url): **string** (nullable = ***false***)
 |    |-- [place_type](#place-place_type): **string** (nullable = ***false***)
 |    |-- [name](#place-name): **string** (nullable = ***false***)
 |    |-- [full_name](#place-full_name): **string** (nullable = ***false***)
 |    |-- [country_code](#place-country_code): **string** (nullable = ***false***)
 |    |-- [country](#place-country): **string** (nullable = ***false***)
 |    |-- [bounding_box](#place-bounding_box): **struct** (nullable = ***false***)
 |    |    |-- [coordinates](#place-bounding_box-coordinates): **array** (nullable = ***false***)
 |    |    |    |-- element: **array** (containsNull = ***false***)
 |    |    |    |    |-- element: **array** (containsNull = ***false***)
 |    |    |    |    |    |-- element: **double** (containsNull = ***false***)
 |    |    |-- [type](#place-bounding_box-type): **string** (nullable = ***false***)
 |-- [quoted_status_id](#quoted_status_id): **long** (nullable = ***false***)
 |-- [quoted_status_id_str](#quoted_status_id_str): **string** (nullable = ***false***)
 |-- [is_quote_status](#is_quote_status): **boolean** (nullable = ***false***)
 |-- [quote_count](#quote_count): **long** (nullable = ***true***)
 |-- [reply_count](#reply_count): **long** (nullable = ***false***)
 |-- [retweet_count](#retweet_count): **long** (nullable = ***false***)
 |-- [favorite_count](#favorite_count): **long** (nullable = ***true***)
 |-- [entities](#entities): **struct** (nullable = ***false***)
 |    |-- [hashtags](#entities-hashtags): **array** (nullable = ***false***)
 |    |    |-- element: **struct** (containsNull = ***true***)
 |    |    |    |-- [indices](#entities-hashtags-indices): **array** (nullable = ***true***)
 |    |    |    |    |-- element: **long** (containsNull = ***true***)
 |    |    |    |-- [text](#entities-hashtags-text): **string** (nullable = ***true***)
 |    |-- [media](#entities-media): **array** (nullable = ***false***)
 |    |    |-- element: **struct** (containsNull = ***true***)
 |    |    |    |-- [additional_media_info](#entities-media-additional_media_info): **struct** (nullable = ***true***)
 |    |    |    |    |-- [description](#entities-media-additional_media_info-description): **string** (nullable = ***false***)
 |    |    |    |    |-- [embeddable](#entities-media-additional_media_info-embeddable): **boolean** (nullable = ***false***)
 |    |    |    |    |-- [monetizable](#entities-media-additional_media_info-monetizable): **boolean** (nullable = ***false***)
 |    |    |    |    |-- [title](#entities-media-additional_media_info-title): **string** (nullable = ***false***)
 |    |    |    |-- [display_url](#entities-media-display_url): **string** (nullable = ***false***)
 |    |    |    |-- [expanded_url](#entities-media-expanded_url): **string** (nullable = ***false***)
 |    |    |    |-- [id](#entities-media-id): **long** (nullable = ***false***)
 |    |    |    |-- [id_str](#entities-media-id_str): **string** (nullable = ***false***)
 |    |    |    |-- [indices](#entities-media-indices): **array** (nullable = ***false***)
 |    |    |    |    |-- element: **long** (containsNull = ***false***)
 |    |    |    |-- [media_url](#entities-media-media_url): **string** (nullable = ***false***)
 |    |    |    |-- [media_url_https](#entities-media-media_url_https): **string** (nullable = ***false***)
 |    |    |    |-- [sizes](#entities-media-sizes): **struct** (nullable = ***false***)
 |    |    |    |    |-- [large](#entities-media-size-large): **struct** (nullable = ***false***)
 |    |    |    |    |    |-- [h](#entities-media-size-h): **long** (nullable = ***false***)
 |    |    |    |    |    |-- [w](#entities-media-size-w): **long** (nullable = ***false***)
 |    |    |    |    |    |-- [resize](#entities-media-size-resize): **string** (nullable = ***false***)
 |    |    |    |    |-- [medium](#entities-media-size-medium): **struct** (nullable = ***false***)
 |    |    |    |    |    |-- [h](#entities-media-size-h): **long** (nullable = ***false***)
 |    |    |    |    |    |-- [w](#entities-media-size-w): **long** (nullable = ***false***)
 |    |    |    |    |    |-- [resize](#entities-media-size-resize): **string** (nullable = ***false***)
 |    |    |    |    |-- [small](#entities-media-size-small): **struct** (nullable = ***false***)
 |    |    |    |    |    |-- [h](#entities-media-size-h): **long** (nullable = ***false***)
 |    |    |    |    |    |-- [w](#entities-media-size-w): **long** (nullable = ***false***)
 |    |    |    |    |    |-- [resize](#entities-media-size-resize): **string** (nullable = ***false***)
 |    |    |    |    |-- [thumb](#entities-media-size-thumb): **struct** (nullable = ***false***)
 |    |    |    |    |    |-- [h](#entities-media-size-h): **long** (nullable = ***false***)
 |    |    |    |    |    |-- [w](#entities-media-size-w): **long** (nullable = ***false***)
 |    |    |    |    |    |-- [resize](#entities-media-size-resize): **string** (nullable = ***false***)
 |    |    |    |-- [source_status_id](#entities-media-source_status_id): **long** (nullable = ***true***)
 |    |    |    |-- [source_status_id_str](#entities-media-source_status_id_str): **string** (nullable = ***true***)
 |    |    |    |-- [type](#entities-media-type): **string** (nullable = ***false***)
 |    |    |    |-- [url](#entities-media-url): **string** (nullable = ***false***)
 |    |    |    |-- video_info: struct (nullable = true)
 |    |    |    |    |-- aspect_ratio: array (nullable = true)
 |    |    |    |    |    |-- element: long (containsNull = true)
 |    |    |    |    |-- duration_millis: long (nullable = true)
 |    |    |    |    |-- variants: array (nullable = true)
 |    |    |    |    |    |-- element: struct (containsNull = true)
 |    |    |    |    |    |    |-- bitrate: long (nullable = true)
 |    |    |    |    |    |    |-- content_type: string (nullable = true)
 |    |    |    |    |    |    |-- url: string (nullable = true)
 |    |-- [polls](#entities-polls): **array** (nullable = ***false***)
 |    |    |-- element: **struct** (containsNull = ***true***)
 |    |    |    |-- [duration_minutes](#entities-poll-duration_minutes): **long** (nullable = ***false***)
 |    |    |    |-- [end_datetime](#entities-poll-end_datetime): **string** (nullable = ***false***)
 |    |    |    |-- [options](#entities-poll-options): **array** (nullable = ***false***)
 |    |    |    |    |-- element: struct (containsNull = true)
 |    |    |    |    |    |-- position: long (nullable = true)
 |    |    |    |    |    |-- text: string (nullable = true)
 |    |-- [symbols](#entities-symbols): **array** (nullable = ***false***)
 |    |    |-- element: **struct** (containsNull = ***true***)
 |    |    |    |-- [indices](#entities-symbol-indices): **array** (nullable = ***true***)
 |    |    |    |    |-- element: long (containsNull = ***false***)
 |    |    |    |-- [text](#entities-symbol-text): **string** (nullable = ***false***)
 |    |-- [urls](#entities-urls): **array** (nullable = ***false***)
 |    |    |-- element: struct (containsNull = true)
 |    |    |    |-- [display_url](#entities-url-display_url): **string** (nullable = ***false***)
 |    |    |    |-- [expanded_url](#entities-url-expanded_url): **string** (nullable = ***false***)
 |    |    |    |-- [indices](#entities-url-indices): **array** (nullable = ***false***)
 |    |    |    |    |-- element: **long** (containsNull = ***false***)
 |    |    |    |-- [unwound](#entities-urls-unwound): struct (nullable = true)
 |    |    |    |    |-- [description](#entities-urls-unwound-description): string (nullable = true)
 |    |    |    |    |-- [status](#entities-urls-unwound-status): long (nullable = true)
 |    |    |    |    |-- [title](#entities-urls-unwound-title): string (nullable = true)
 |    |    |    |    |-- [url](#entities-urls-unwound-url): string (nullable = true)
 |    |    |    |-- [url](#entities-url-url): string (nullable = true)
 |    |-- [user_mentions](#entities-user_mentions): **array** (nullable = ***false***)
 |    |    |-- element: **struct** (containsNull = ***true***)
 |    |    |    |-- [id](#entities-user_mention-id): **long (nullable = ***false***)
 |    |    |    |-- [id_str](#entities-user_mention-id_str): **string** (nullable = ***false***)
 |    |    |    |-- [indices](#entities-user_mention-indices): **array** (nullable = ***false***)
 |    |    |    |    |-- element: **long** (containsNull = ***false***)
 |    |    |    |-- [name](#entities-user_mention-name): **string** (nullable = ***false***)
 |    |    |    |-- [screen_name](#entities-user_mention-screen_name): **string** (nullable = ***false***)
 |-- [extended_entities](#extended_entities): struct (nullable = true)
 |    |-- media: array (nullable = true)
 |    |    |-- element: struct (containsNull = true)
 |    |    |    |-- additional_media_info: struct (nullable = true)
 |    |    |    |    |-- description: string (nullable = true)
 |    |    |    |    |-- embeddable: boolean (nullable = true)
 |    |    |    |    |-- monetizable: boolean (nullable = true)
 |    |    |    |    |-- title: string (nullable = true)
 |    |    |    |-- display_url: string (nullable = true)
 |    |    |    |-- expanded_url: string (nullable = true)
 |    |    |    |-- id: long (nullable = true)
 |    |    |    |-- id_str: string (nullable = true)
 |    |    |    |-- indices: array (nullable = true)
 |    |    |    |    |-- element: long (containsNull = true)
 |    |    |    |-- media_url: string (nullable = true)
 |    |    |    |-- media_url_https: string (nullable = true)
 |    |    |    |-- sizes: struct (nullable = true)
 |    |    |    |    |-- large: struct (nullable = true)
 |    |    |    |    |    |-- h: long (nullable = true)
 |    |    |    |    |    |-- resize: string (nullable = true)
 |    |    |    |    |    |-- w: long (nullable = true)
 |    |    |    |    |-- medium: struct (nullable = true)
 |    |    |    |    |    |-- h: long (nullable = true)
 |    |    |    |    |    |-- resize: string (nullable = true)
 |    |    |    |    |    |-- w: long (nullable = true)
 |    |    |    |    |-- small: struct (nullable = true)
 |    |    |    |    |    |-- h: long (nullable = true)
 |    |    |    |    |    |-- resize: string (nullable = true)
 |    |    |    |    |    |-- w: long (nullable = true)
 |    |    |    |    |-- thumb: struct (nullable = true)
 |    |    |    |    |    |-- h: long (nullable = true)
 |    |    |    |    |    |-- resize: string (nullable = true)
 |    |    |    |    |    |-- w: long (nullable = true)
 |    |    |    |-- source_status_id: long (nullable = true)
 |    |    |    |-- source_status_id_str: string (nullable = true)
 |    |    |    |-- type: string (nullable = true)
 |    |    |    |-- url: string (nullable = true)
 |    |    |    |-- video_info: struct (nullable = true)
 |    |    |    |    |-- aspect_ratio: array (nullable = true)
 |    |    |    |    |    |-- element: long (containsNull = true)
 |    |    |    |    |-- duration_millis: long (nullable = true)
 |    |    |    |    |-- variants: array (nullable = true)
 |    |    |    |    |    |-- element: struct (containsNull = true)
 |    |    |    |    |    |    |-- bitrate: long (nullable = true)
 |    |    |    |    |    |    |-- content_type: string (nullable = true)
 |    |    |    |    |    |    |-- url: string (nullable = true)
 |-- favorited: boolean (nullable = true)
 |-- retweeted: boolean (nullable = true)
 |-- possibly_sensitive: boolean (nullable = true)
 |-- filter_level: string (nullable = true)
 |-- lang: string (nullable = true)
</pre></big>

-----------------------------

### Fields and Attributes Description

+ #### created_at
  UTC time when this Tweet was created.  
  
  *Type: String*  

  Example:
  ```json
  "created_at": "Wed Oct 10 20:19:24 +0000 2018"
  ```
  [back](#Tweet-JSON-Schema)

-----------------------------
+ #### id
  The integer representation of the unique identifier for this Tweet. This number is greater than 53 bits and some programming languages may have difficulty/silent defects in interpreting it. Using a signed 64 bit integer for storing this identifier is safe. Use id_str for fetching the identifier to stay on the safe side.  
  
  *Type: Int64*  

  Example:
  ```json
  "id":1050118621198921728
  ```
  [back](#Tweet-JSON-Schema)

-----------------------------
+ #### id_str
  The string representation of the unique identifier for this Tweet. Implementations should use this rather than the large integer in id.  
  
  *Type: String*  

  Example:
  ```json
  "id_str":"1050118621198921728"
  ```
  [back](#Tweet-JSON-Schema)

-----------------------------
+ #### text
  The actual UTF-8 text of the status update. See [twitter-text](https://github.com/twitter/twitter-text/blob/master/rb/lib/twitter-text/regex.rb) for details on what characters are currently considered valid.  

  *Type: String*  

  Example:
  ```json
  "text":"To make room for more expression, we will now count all emojis as equal—including those with gender‍‍‍ ‍‍and skin t… https://t.co/MkGjXf9aXm"
  ```
  [back](#Tweet-JSON-Schema)

-----------------------------
+ #### source
  Utility used to post the Tweet, as an HTML-formatted string. Tweets from the Twitter website have a source value of web.  
  
  *Type: String*  

  Example:
  ```json
  "source":"Twitter Web Client"
  ```
  [back](#Tweet-JSON-Schema)

-----------------------------
+ #### truncated
  Indicates whether the value of the [text](#text) parameter was truncated, for example, as a result of a retweet exceeding the original Tweet text length limit of 140 characters. Truncated text will end in ellipsis, like this ```...``` Since Twitter now rejects long Tweets vs truncating them, the large majority of Tweets will have this set to **false** . Note that while native retweets may have their toplevel text property shortened, the original **text** will be available under the [retweeted_status](#retweeted_status) object and the **truncated** parameter will be set to the value of the original status (in most cases, false ).  
  
  *Type: Boolean*  

  Example:
  ```json
  "truncated":true
  ```
  [back](#Tweet-JSON-Schema)

-----------------------------
+ #### in_reply_to_status_id
  *Nullable*. If the represented Tweet is a reply, this field will contain the integer representation of the original Tweet’s ID.  

  *Type: Int64*  

  Example:
  ```json
  "in_reply_to_status_id":1051222721923756032
  ```
  [back](#Tweet-JSON-Schema)

-----------------------------
+ #### in_reply_to_status_id_str 
  *Nullable*. If the represented Tweet is a reply, this field will contain the string representation of the original Tweet’s ID.  

  *Type: String*  

  Example:
  ```json
  "in_reply_to_status_id_str":"1051222721923756032"
  ```
  [back](#Tweet-JSON-Schema)

-----------------------------
+ #### in_reply_to_user_id
  *Nullable*. If the represented Tweet is a reply, this field will contain the integer representation of the original Tweet’s author ID. This will not necessarily always be the user directly mentioned in the Tweet.  

  *Type: Int64*  

  Example:
  ```json
  "in_reply_to_user_id":6253282
  ```
  [back](#Tweet-JSON-Schema)

-----------------------------
+ #### in_reply_to_user_id_str
  *Nullable*. If the represented Tweet is a reply, this field will contain the string representation of the original Tweet’s author ID. This will not necessarily always be the user directly mentioned in the Tweet.  

  *Type: String*  

  Example:
  ```json
  "in_reply_to_user_id_str":"6253282"
  ```
  [back](#Tweet-JSON-Schema)

-----------------------------
+ #### in_reply_to_screen_name
  *Nullable*. If the represented Tweet is a reply, this field will contain the screen name of the original Tweet’s author.  

  *Type: String*  

  Example:
  ```json
  "in_reply_to_screen_name":"twitterapi"
  ```
  [back](#Tweet-JSON-Schema)

-----------------------------
+ #### user
   The user who posted this Tweet.  
   *Type: Struct*
   
   
   + ##### user-id  
     *Type: Int64*  
   
     The integer representation of the unique identifier for this User.       This number is greater than 53 bits and some programming languages       may have difficulty/silent defects in interpreting it. Using a           signed 64 bit integer for storing this identifier is safe. Use           id_str for fetching the identifier to stay on the safe side.
      
        Example:
        ```json
        "id": 6253282
        ```   
        [back](#Tweet-JSON-Schema)
        
   + ##### user-id_str  
     *Type: Int64*  
   
     The string representation of the unique identifier for this User.       Implementations should use this rather than the large, possibly         un-consumable integer in id.
        
        Example:
        ```json
        "id_str": "6253282"
        ```
        [back](#Tweet-JSON-Schema)
        
   + ##### user-name  
     *Type: String*  
   
     The name of the user, as they’ve defined it. Not necessarily a           person’s name. Typically capped at 50 characters, but subject to         change. Example:

        Example:
        ```json
        "name": "Twitter API"
        ```
        [back](#Tweet-JSON-Schema)
        
   + ##### user-screen_name  
     *Type: String*  
   
     The screen name, handle, or alias that this user identifies              themselves with. screen_names are unique but subject to change. Use      **id_str** as a user identifier whenever possible. Typically a          maximum of 15 characters long, but some historical accounts may exist    with longer names.
   
        Example:
        ```json
        "screen_name": "twitterapi"
        ```
        [back](#Tweet-JSON-Schema)
        
   + ##### user-location  
     *Type: String*  
   
     *Nullable*. The user-defined location for this account’s profile. Not    necessarily a location, nor machine-parseable. This field will          occasionally be fuzzily interpreted by the Search service.
   
        Example:
        ```json
        "location": "San Francisco, CA"
        ```
        [back](#Tweet-JSON-Schema)
        
   + ##### user-derived  
     *Type: Arrays of Enrichment Objects*  
   
     Enterprise APIs only Collection of Enrichment metadata derived for user. Provides the Profile Geo Enrichment metadata. See referenced documentation for more information, including JSON data dictionaries  
   
        Example:
        ```json
         "derived": {
            "locations": [
                {
                    "country": "United States",
                    "country_code": "US",
                    "locality": "Birmingham",
                    "region": "Alabama",
                    "sub_region": "Jefferson County",
                    "full_name": "Birmingham, Alabama, United States",
                    "geo": {
                        "coordinates": [
                            -86.80249,
                            33.52066
                        ],
                        "type": "point"
                    }
                }
            ]
        }
        ```
        + ##### user-derived-locations  
          - ###### user-derived-locations-country  
            *Type: String*  
            
            The country location for where the user that created the Tweet is from.
            
            Example:
            ```json
            "United States"
            ```
            [back](#Tweet-JSON-Schema)
            
          - ###### user-derived-locations-country_code  
            *Type: String*  
            
            A two-letter [ISO-3166](https://www.iso.org/iso-3166-country-codes.html) country code that corresponds to the country location for where the user that created the Tweet is from.
            
            Example:
            ```json
            "US"
            ```
            [back](#Tweet-JSON-Schema)
            
          - ###### user-derived-locations-locality  
            *Type: String*  
            
            The locality location (generally city) for where the user that created the Tweet is from.
            
            Example:
            ```json
            "Birmingham"
            ```
            [back](#Tweet-JSON-Schema)
            
          - ###### user-derived-locations-region  
            *Type: String*  
            
            The region location (generally state/province) for where the user that created the Tweet is from.
            
            Example:
            ```json
            "Alabama"
            ```
            [back](#Tweet-JSON-Schema)
            
          - ###### user-derived-locations-sub_region  
            *Type: String*  
            
            The sub-region location (generally county) for where the user that created the Tweet is from.
            
            Example:
            ```json
            "Jefferson County"
            ```
            [back](#Tweet-JSON-Schema)
            
          - ###### user-derived-locations-full_name  
            *Type: String*  
            
            The full name (excluding sub-region) for where the user that created the Tweet is from.
            
            Example:
            ```json
            "JBirmingham, Alabama, United States"
            ```
            [back](#Tweet-JSON-Schema)
            
          - ###### user-derived-locations-geo  
            An array that includes a lat/long value for a coordinate that corresponds to the lowers granularity location for where the user that created the Tweet is from.
            
            Example:
            ```json
             "geo": {
                        "coordinates": [
                            -86.80249,
                            33.52066
                        ],
                        "type": "point"
                    }
            ```
            [back](#Tweet-JSON-Schema)
      
   + ##### user-url  
     *Type: String*  
   
     Nullable . A URL provided by the user in association with their profile.
   
        Example:
        ```json
        "url": "https://developer.twitter.com"
        ```
        [back](#Tweet-JSON-Schema)
        
   + ##### user-description  
     *Type: String*  
   
     Nullable . The user-defined UTF-8 string describing their account.
   
        Example:
        ```json
        "description": "The Real Twitter API."
        ```
        [back](#Tweet-JSON-Schema)
        
   + ##### user-protected  
     *Type: Boolean*  
   
     When true, indicates that this user has chosen to protect their Tweets. See [About Public and Protected Tweets](https://help.twitter.com/en/safety-and-security/public-and-protected-tweets)
   
        Example:
        ```json
        "protected": true
        ```
        [back](#Tweet-JSON-Schema)
        
   + ##### user-verified  
     *Type: Boolean*  
   
     When true, indicates that the user has a verified account. See [Verified Accounts](https://help.twitter.com/en/managing-your-account/about-twitter-verified-accounts).
   
        Example:
        ```json
        "verified": false
        ```
        [back](#Tweet-JSON-Schema)
        
   + ##### user-followers_count  
     *Type: Int*  
   
     The number of followers this account currently has. Under certain conditions of duress, this field will temporarily indicate “0”.
   
        Example:
        ```json
        "followers_count": 21
        ```
        [back](#Tweet-JSON-Schema)
        
   + ##### user-friends_count  
     *Type: Int*  
   
     The number of users this account is following (AKA their “followings”). Under certain conditions of duress, this field will temporarily indicate “0”.
   
        Example:
        ```json
        "friends_count": 32
        ```
        [back](#Tweet-JSON-Schema)

   + ##### user-listed_count  
     *Type: Int*  
   
     The number of public lists that this user is a member of.
   
        Example:
        ```json
        "listed_count": 9274
        ```
        [back](#Tweet-JSON-Schema)

   + ##### user-favourites_count  
     *Type: Int*  
   
     The number of Tweets this user has liked in the account’s lifetime. British spelling used in the field name for historical reasons.
   
        Example:
        ```json
        "favourites_count": 13
        ```
        [back](#Tweet-JSON-Schema)

   + ##### user-statuses_count  
     *Type: Int*  
   
     The number of Tweets (including retweets) issued by the user.
   
        Example:
        ```json
        "statuses_count": 42
        ```
        [back](#Tweet-JSON-Schema)

   + ##### user-created_at  
     *Type: String*  
   
     The UTC datetime that the user account was created on Twitter.
   
        Example:
        ```json
        "created_at": "Mon Nov 29 21:18:15 +0000 2010"
        ```
        [back](#Tweet-JSON-Schema)

   + ##### user-profile_banner_url  
     *Type: String*  
   
     The HTTPS-based URL pointing to the standard web representation of the user’s uploaded profile banner. By adding a final path element of the URL, it is possible to obtain different image sizes optimized for specific displays. For size variants, please see [User Profile Images and Banners](https://developer.twitter.com/en/docs/accounts-and-users/user-profile-images-and-banners).
   
        Example:
        ```json
        "profile_banner_url": "https://si0.twimg.com/profile_banners/819797/1348102824"
        ```
        [back](#Tweet-JSON-Schema)

   + ##### user-profile_image_url_https  
     *Type: String*  
   
     A HTTPS-based URL pointing to the user’s profile image.
   
        Example:
        ```json
        "profile_image_url_https":"https://abs.twimg.com/sticky/default_profile_images/default_profile_normal.png"
        ```
        [back](#Tweet-JSON-Schema)

   + ##### user-default_profile  
     *Type: Boolean*  
   
     When true, indicates that the user has not altered the theme or background of their user profile.
   
        Example:
        ```json
        "default_profile": false        
        ```
        [back](#Tweet-JSON-Schema)

   + ##### user-default_profile_image  
     *Type: Boolean*  
   
     When true, indicates that the user has not uploaded their own profile image and a default image is used instead.
   
        Example:
        ```json
        "default_profile_image": false        
        ```
        [back](#Tweet-JSON-Schema)

   + ##### user-withheld_in_countries  
     *Type: Array of String*  
   
     When present, indicates a list of uppercase two-letter country codes this content is withheld from. Twitter supports the following non-country values for this field:

     “XX” - Content is withheld in all countries “XY” - Content is withheld due to a DMCA request.
   
        Example:
        ```json
        "withheld_in_countries": ["GR", "HK", "MY"]        
        ```
        [back](#Tweet-JSON-Schema)

   + ##### user-withheld_scope  
     *Type: String*  
   
     When present, indicates that the content being withheld is a “user.”
   
        Example:
        ```json
        "withheld_scope": "user"        
        ```
        [back](#Tweet-JSON-Schema)

-----------------------------
+ #### coordinates
  *Nullable*. Represents the geographic location of this Tweet as reported by the user or client application. The inner coordinates array is formatted as [geoJSON](https://geojson.org/) (longitude first, then latitude).   
  
  *Type: struct*  

  Example:
  ```json
  "coordinates":
  {
    "coordinates":
    [
        -75.14310264,
        40.05701649
    ],
    "type":"Point"
  }
  ```
  [back](#Tweet-JSON-Schema)

   + ###### coordinates-coordinates  
     *Type: Collection of Float*  
   
     The longitude and latitude of the Tweet’s location, as a collection in the form [longitude, latitude].
   
        Example:
        ```json
        "coordinates":[-97.51087576,35.46500176]       
        ```
        [back](#Tweet-JSON-Schema)

   + ######  coordinates-coordinates-type  
     *Type: String*  
   
     The type of data encoded in the coordinates property. This will be “Point” for Tweet coordinates fields.
   
        Example:
        ```json
        "type": "Point"       
        ```
        [back](#Tweet-JSON-Schema)


-----------------------------
+ #### place
  *Nullable* When present, indicates that the tweet is associated (but not necessarily originating from) a Place.   
  
  *Type: Places*  

  Example:
  ```json
  "place":
  {
   "attributes":{},
   "bounding_box":
   {
     "coordinates":
     [[
           [-77.119759,38.791645],
           [-76.909393,38.791645],
           [-76.909393,38.995548],
           [-77.119759,38.995548]
     ]],
     "type":"Polygon"
   },
   "country":"United States",
   "country_code":"US",
   "full_name":"Washington, DC",
   "id":"01fbe706f872cb32",
   "name":"Washington",
   "place_type":"city",
   "url":"http://api.twitter.com/1/geo/id/0172cb32.json"
  }
  ```
  [back](#Tweet-JSON-Schema)

   + ##### place-id  
     *Type: String*  
   
     ID representing this place. Note that this is represented as a string, not an integer.
   
        Example:
        ```json
        "id":"01a9a39529b27f36"       
        ```
        [back](#Tweet-JSON-Schema)

   + ##### place-url  
     *Type: String*  
   
     URL representing the location of additional place metadata for this place.
   
        Example:
        ```json
        "url":"https://api.twitter.com/1.1/geo/id/01a9a39529b27f36.json"       
        ```
        [back](#Tweet-JSON-Schema)

   + ##### place-place_type  
     *Type: String*  
   
     The type of location represented by this place.
   
        Example:
        ```json
        "place_type":"city"       
        ```
        [back](#Tweet-JSON-Schema)

   + ##### place-name  
     *Type: String*  
   
     Short human-readable representation of the place’s name.
   
        Example:
        ```json
        "name":"Manhattan"       
        ```
        [back](#Tweet-JSON-Schema)

   + ##### place-full_name  
     *Type: String*  
   
     Full human-readable representation of the place’s name.
   
        Example:
        ```json
        "full_name":"Manhattan, NY"       
        ```
        [back](#Tweet-JSON-Schema)

   + ##### place-country_code  
     *Type: String*  
   
     Shortened country code representing the country containing this place.
   
        Example:
        ```json
        "country_code":"US"       
        ```
        [back](#Tweet-JSON-Schema)

   + ##### place-country  
     *Type: String*  
   
     Name of the country containing this place.
   
        Example:
        ```json
        "country":"United States"       
        ```
        [back](#Tweet-JSON-Schema)

   + ##### place-bounding_box  
     *Type: String*  
   
     A bounding box of coordinates which encloses this place.
   
        Example:
        ```json
        {
         "bounding_box": {
         "coordinates": [
         [
          [
           -74.026675,
           40.683935
          ],
          [
           -74.026675,
           40.877483
          ],
          [
           -73.910408,
           40.877483
          ],
          [
           -73.910408,
           40.3935
          ]
        ]],
        "type": "Polygon"}
      }       
     ```
        [back](#Tweet-JSON-Schema)

        + ###### place-bounding_box-coordinates  
          *Type: Array of Array of Array of Float*  
            
            A series of longitude and latitude points, defining a box which will contain the Place entity this bounding box is related to. Each point is an array in the form of [longitude, latitude]. Points are grouped into an array per bounding box. Bounding box arrays are wrapped in one additional array to be compatible with the polygon notation. 
            
            Example:
            ```json
            {
              "coordinates": [
                [
                  [
                    -74.026675,
                    40.683935
                  ],
                  [
                    -74.026675,
                    40.877483
                  ],
                  [
                    -73.910408,
                    40.877483
                  ],
                  [
                    -73.910408,
                    40.3935
                  ]
                ]
              ]
            }
            ```
            [back](#Tweet-JSON-Schema)
            
        + ###### place-bounding_box-type  
          *Type: String*  
            
            The type of data encoded in the coordinates property. This will be “Polygon” for bounding boxes and “Point” for Tweets with exact coordinates. 
            
            Example:
            ```json
            "type":"Polygon"
            ```
            [back](#Tweet-JSON-Schema)

-----------------------------
+ #### quoted_status_id
  This field only surfaces when the Tweet is a quote Tweet. This field contains the integer value Tweet ID of the quoted Tweet.  
  
  *Type: Int64*  

  Example:
  ```json
  "quoted_status_id":1050119905717055488
  ```
  [back](#Tweet-JSON-Schema)

-----------------------------
+ #### quoted_status_id_str
  This field only surfaces when the Tweet is a quote Tweet. This is the string representation Tweet ID of the quoted Tweet.  
  
  *Type: String*  

  Example:
  ```json
  "quoted_status_id_str":"1050119905717055488"
  ```
  [back](#Tweet-JSON-Schema)

-----------------------------
+ #### is_quote_status
  Indicates whether this is a Quoted Tweet.  
  
  *Type: Boolean*  

  Example:
  ```json
  "is_quote_status":false
  ```
  [back](#Tweet-JSON-Schema)

-----------------------------
+ #### quoted_status
  This field only surfaces when the Tweet is a quote Tweet. This attribute contains the Tweet object of the original Tweet that was quoted.  
  
  *Type: Tweet*  

  [back](#Tweet-JSON-Schema)

-----------------------------
+ #### retweeted_status
  Users can amplify the broadcast of Tweets authored by other users by retweeting . Retweets can be distinguished from typical Tweets by the existence of a retweeted_status attribute. This attribute contains a representation of the original Tweet that was retweeted. Note that retweets of retweets do not show representations of the intermediary retweet, but only the original Tweet. (Users can also unretweet a retweet they created by deleting their retweet.).  
  
  *Type: Tweet*  

  [back](#Tweet-JSON-Schema)

-----------------------------
+ #### quote_count
  *Nullable*. Indicates approximately how many times this Tweet has been quoted by Twitter users.   
  
  *Type: Integer*  

  Example:
  ```json
  "quote_count":33
  ```
  Note: This object is only available with the Premium and Enterprise tier products.  
  
  [back](#Tweet-JSON-Schema)

-----------------------------
+ #### reply_count
  Number of times this Tweet has been replied to.    
  
  *Type: Int*  

  Example:
  ```json
  "reply_count":30
  ```
  Note: This object is only available with the Premium and Enterprise tier products.  
  
  [back](#Tweet-JSON-Schema)

-----------------------------
+ #### retweet_count
  Number of times this Tweet has been retweeted.  
  
  *Type: Int*  

  Example:
  ```json
  "retweet_count":160
  ```    
  [back](#Tweet-JSON-Schema)

-----------------------------
+ #### favorite_count
  *Nullable*. Indicates approximately how many times this Tweet has been liked by Twitter users.  
  
  *Type: Int*  

  Example:
  ```json
  "favorite_count":295
  ```    
  [back](#Tweet-JSON-Schema)

-----------------------------
+ #### entities
  Entities which have been parsed out of the text of the Tweet.  
  
  *Type: Int*  

  Example:
  ```json
  "favorite_count":295
  ```    
  [back](#Tweet-JSON-Schema)

   + ##### entities-hashtags  
     *Type: Array of Hashtag Objects*  
   
     Represents hashtags which have been parsed out of the Tweet text.
     The [entities](#entities) section will contain a hashtags array containing an object for every hashtag included in the Tweet body, and include an empty array if no hashtags are present.
   
        Example:
        ```json
        {
          "hashtags": [
            {
              "indices": [
                32,
                38
              ],
              "text": "nodejs"
            }
          ]
        }
        ```
        [back](#Tweet-JSON-Schema)

        + ###### entities-hashtags-indices  
          *Type: Array of Int*  
            
            An array of integers indicating the offsets within the Tweet text where the hashtag begins and ends. The first integer represents the location of the # character in the Tweet text string. The second integer represents the location of the first character after the hashtag. Therefore the difference between the two numbers will be the length of the hashtag name plus one (for the ‘#’ character) 
            
            Example:
            ```json
            "indices":[32,38]
            ```
            [back](#Tweet-JSON-Schema)

        + ###### entities-hashtags-text  
          *Type: String*  
            
            Name of the hashtag, minus the leading ‘#’ character. 
            
            Example:
            ```json
            "text":"nodejs"
            ```
            [back](#Tweet-JSON-Schema)

   + ##### entities-media  
     *Type: Array of Media Objects*  
   
     Represents media elements uploaded with the Tweet.
     The entities section will contain a media array containing a single media object if any media object has been ‘attached’ to the Tweet. If no native media has been attached, there will be no media array in the entities. For the following reasons the [extended_entities](#extended_entities) section should be used to process Tweet native media.
     
     Note:
      - Media type will always indicate ‘photo’ even in cases of a video and GIF being attached to Tweet.
      - Even though up to four photos can be attached, only the first one will be listed in the entities section.
   
     Example:
     ```json
        {
          "media": [
            {
              "display_url": "pic.twitter.com/5J1WJSRCy9",
              "expanded_url": "https://twitter.com/nolan_test/status/930077847535812610/photo/1",
              "id": 9.300778475358126e17,
              "id_str": "930077847535812610",
              "indices": [
                  13,
                  36
              ],
              "media_url": "http://pbs.twimg.com/media/DOhM30VVwAEpIHq.jpg",
              "media_url_https": "https://pbs.twimg.com/media/DOhM30VVwAEpIHq.jpg"
              "sizes": {
                  "thumb": {
                       "h": 150,
                       "resize": "crop",
                       "w": 150
                  },
                  "large": {
                      "h": 1366,
                      "resize": "fit",
                      "w": 2048
                  },
                  "medium": {
                      "h": 800,
                      "resize": "fit",
                      "w": 1200
                  },
                  "small": {
                      "h": 454,
                      "resize": "fit",
                      "w": 680
                  }
              },
              "type": "photo",      
              "url": "https://t.co/5J1WJSRCy9",
            }
          ]
        }
     ```
     [back](#Tweet-JSON-Schema)

        + ###### entities-media-display_url  
          *Type: String*  
            
            URL of the media to display to clients.  
            
            Example:
            ```json
            "display_url":"pic.twitter.com/rJC5Pxsu"
            ```
            [back](#Tweet-JSON-Schema)

        + ###### entities-media-expanded_url  
          *Type: String*  
            
            An expanded version of display_url. Links to the media display page.  
            
            Example:
            ```json
            "expanded_url": "http://twitter.com/yunorno/status/114080493036773378/photo/1"
            ```
            [back](#Tweet-JSON-Schema)

        + ##### entities-media-id  
          *Type: Int64*  
            
            ID of the media expressed as a 64-bit integer.   
            
            Example:
            ```json
            "id":114080493040967680
            ```
            [back](#Tweet-JSON-Schema)

        + ##### entities-media-id_str  
          *Type: String*  
            
            ID of the media expressed as a string.   
            
            Example:
            ```json
            "id":"114080493040967680"
            ```
            [back](#Tweet-JSON-Schema)

        + ##### entities-media-indices  
          *Type: Array of Int*  
            
            An array of integers indicating the offsets within the Tweet text where the URL begins and ends. The first integer represents the location of the first character of the URL in the Tweet text. The second integer represents the location of the first non-URL character occurring after the URL (or the end of the string if the URL is the last part of the Tweet text).   
            
            Example:
            ```json
            "indices":[15,35]
            ```
            [back](#Tweet-JSON-Schema)

        + ##### entities-media-media_url  
          *Type: String*  
            
            An http:// URL pointing directly to the uploaded media file.   
            
            Example:
            ```json
            "media_url":"http://pbs.twimg.com/media/DOhM30VVwAEpIHq.jpg"
            ```
            For media in direct messages, media_url_https must be accessed by signing a request with the user’s access token using OAuth 1.0A.

           It is not possible to access images via an authenticated twitter.com session.

          You cannot directly embed these images in a web page.
            
            [back](#Tweet-JSON-Schema)

        + ##### entities-media-media_url_https  
          *Type: String*  
            
            An https:// URL pointing directly to the uploaded media file, for embedding on https pages.    
            
            Example:
            ```json
            "media_url_https":"https://p.twimg.com/AZVLmp-CIAAbkyy.jpg"
            ```
            For media in direct messages, media_url_https must be accessed by signing a request with the user’s access token using OAuth 1.0A.

           It is not possible to access images via an authenticated twitter.com session.

          You cannot directly embed these images in a web page.
            
            [back](#Tweet-JSON-Schema)

        + ##### entities-media-sizes  
          *Type: Size Object*  
            
            An object showing available sizes for the media file.     
            
            Example:
            ```json
            {
              "sizes": {
                "thumb": {
                  "h": 150,
                  "resize": "crop",
                  "w": 150
                },
                "large": {
                  "h": 1366,
                  "resize": "fit",
                  "w": 2048
                },
                "medium": {
                  "h": 800,
                  "resize": "fit",
                  "w": 1200
                },
                "small": {
                  "h": 454,
                  "resize": "fit",
                  "w": 680
                }
              }
            }
            ```          
            [back](#Tweet-JSON-Schema)

            **Media size objects**  
            All Tweets with native media (photos, video, and GIFs) will include a set of ‘thumb’, ‘small’, ‘medium’, and ‘large’ sizes with height and width pixel sizes.

          - ###### entities-media-size-thumb  
            *Type: Size Object*  
            
            Information for a thumbnail-sized version of the media.
            
            Example:
            ```json
             "thumb":{"h":150, "resize":"crop", "w":150}
            ```
            Thumbnail-sized photo media will be limited to fill a 150x150 boundary and cropped.
            
            [back](#Tweet-JSON-Schema)

          - ###### entities-media-size-large  
            *Type: Size Object*  
            
            Information for a large-sized version of the media.
            
            Example:
            ```json
             "large":{"h":1366, "resize":"fit", "w":2048}
            ```
            Large-sized photo media will be limited to fit within a 2048x2048 boundary.
            
            [back](#Tweet-JSON-Schema)

          - ###### entities-media-size-medium  
            *Type: Size Object*  
            
            Information for a medium-sized version of the media.
            
            Example:
            ```json
             "medium":{"h":800, "resize":"fit", "w":1200}
            ```
            Medium-sized photo media will be limited to fit within a 1200x1200 boundary.
            
            [back](#Tweet-JSON-Schema)

          - ###### entities-media-size-small  
            *Type: Size Object*  
            
            Information for a small-sized version of the media.
            
            Example:
            ```json
             "small":{"h":454, "resize":"fit", "w":680}
            ```
            Small-sized photo media will be limited to fit within a 680x680 boundary.
            
            [back](#Tweet-JSON-Schema)

          **Size object**  

            - ###### entities-media-size-w  
              *Type: Int*  
            
              Width in pixels of this size. 
            
              Example:
              ```json
              "w":150
              ```
              [back](#Tweet-JSON-Schema)

            - ###### entities-media-size-h  
              *Type: Int*  
            
              Height in pixels of this size. 
            
              Example:
              ```json
              "h":135
              ```
              [back](#Tweet-JSON-Schema)

            - ###### entities-media-size-resize  
              *Type: String*  
            
              Resizing method used to obtain this size. A value of fit means that the media was resized to fit one dimension, keeping its native aspect ratio. A value of crop means that the media was cropped in order to fit a specific resolution. 
            
              Example:
              ```json
              "resize":"crop"
              ```
              [back](#Tweet-JSON-Schema)

        + ###### entities-media-source_status_id  
          *Type: Int64*  
            
            *Nullable*. For Tweets containing media that was originally associated with a different tweet, this ID points to the original Tweet.    
            
            Example:
            ```json
            "source_status_id": 205282515685081088
            ```
            [back](#Tweet-JSON-Schema)

        + ###### entities-media-source_status_id_str  
          *Type: String*  
            
            *Nullable*. For Tweets containing media that was originally associated with a different tweet, this string-based ID points to the original Tweet.     
            
            Example:
            ```json
            "source_status_id_str": "205282515685081088"
            ```          
            [back](#Tweet-JSON-Schema)

        + ###### entities-media-type  
          *Type: String*  
            
            Type of uploaded media. Possible types include photo, video, and animated_gif.   
            
            Example:
            ```json
            "type":"photo"
            ```          
            [back](#Tweet-JSON-Schema)


        + ###### entities-media-url  
          *Type: String*  
            
            *Wrapped URL for the media link. This corresponds with the URL embedded directly into the raw Tweet text, and the values for the [indices](#entities-media-indices) parameter.     
            
            Example:
            ```json
            "url":"http://t.co/rJC5Pxsu"
            ```          
            [back](#Tweet-JSON-Schema)





   + ##### entities-urls  
     *Type: Array of URL Objects*  
   
     Represents URLs included in the text of a Tweet.
           
     Example (without Enhanced URLs enrichment enabled):
     ```json
        {
          "urls": [
            {
              "indices": [
                32,
                52
              ],
              "url": "http://t.co/IOwBrTZR",
              "display_url": "youtube.com/watch?v=oHg5SJ…",
              "expanded_url": "http://www.youtube.com/watch?v=oHg5SJYRHA0"
            }
          ]
        }
     ```
     Example (with Enhanced URLs enrichment enabled):
     ```json
        {"urls": [
              {
                "url": "https://t.co/D0n7a53c2l",
                "expanded_url": "http://bit.ly/18gECvy",
                "display_url": "bit.ly/18gECvy",
                "unwound": {
                  "url": "https://www.youtube.com/watch?v=oHg5SJYRHA0",
                  "status": 200,
                  "title": "RickRoll'D",
                  "description": "http://www.facebook.com/rickroll548 As long as trolls are still trolling, the Rick will never stop rolling."
                },
                "indices": [
                  62,
                  85
                ]
              }
            ]
        }
     ```



     
     [back](#Tweet-JSON-Schema)
     
     **URL object** 
The entities section will contain a urls array containing an object for every link included in the Tweet body, and include an empty array if no links are present.

        + ###### entities-url-display_url  
          *Type: String*  
            
            URL pasted/typed into Tweet  
            
            Example:
            ```json
            "display_url":"bit.ly/2so49n2"
            ```
            [back](#Tweet-JSON-Schema)

        + ###### entities-url-expanded_url  
          *Type: String*  
            
            Expanded version of `` display_url``.  
            
            Example:
            ```json
            "expanded_url":"http://bit.ly/2so49n2"
            ```
            [back](#Tweet-JSON-Schema)

        + ###### entities-url-indices  
          *Type: Array of Int*  
            
            An array of integers representing offsets within the Tweet text where the URL begins and ends. The first integer represents the location of the first character of the URL in the Tweet text. The second integer represents the location of the first non-URL character after the end of the URL.  
            
            Example:
            ```json
            "indices":[30,53]
            ```
            [back](#Tweet-JSON-Schema)

        + ###### entities-url-url  
          *Type: String*  
            
            Wrapped URL, corresponding to the value embedded directly into the raw Tweet text, and the values for the indices parameter.   
            
            Example:
            ```json
            "url":"https://t.co/yzocNFvJuL"
            ```
            [back](#Tweet-JSON-Schema)

        + ##### entities-url-unwound
                      
            Available only if using the Expanded and/or Enhanced URL enrichments.   
            
            Example:
            ```json
            "unwound" :
            {
             "url" : "https://www.youtube.com/watch?v=oHg5SJYRHA0",
             "status" : 200,
             "title" : "RickRoll'D",
             "description" : "http://www.facebook.com/rickroll548 As long as trolls are still trolling, the Rick will never stop rolling."
           }
           ```
            [back](#Tweet-JSON-Schema)

            + ###### entities-url-unwound-url
              *Type: String*  
              
              The fully unwound version of the link included in the Tweet.   

                Example:
                ```json
                "url":"https://blog.twitter.com/en_us/topics/insights/2016/using-twitter-as-a-go-to-communication-channel-during-severe-weather-events.html"
               ```
                [back](#Tweet-JSON-Schema)

            + ###### entities-url-unwound-status
              *Type: Int*  
              
              Final HTTP status of the unwinding process, a '200' indicating success.

                Example:
                ```json
                200
               ```
                [back](#Tweet-JSON-Schema)

            + ###### entities-url-unwound-title
              *Type: String*  
              
              HTML title for the link.

                Example:
                ```json
                "title":"Using Twitter as a ‘go-to’ communication channel during severe weather"
               ```
                [back](#Tweet-JSON-Schema)

            + ###### entities-url-unwound-description
              *Type: String*  
              
              HTML description for the link.

                Example:
                ```json
                "description":"Using Twitter as a ‘go-to’ communication channel during severe weather"
               ```
                [back](#Tweet-JSON-Schema)


   + ##### entities-user_mentions  
     *Type: Array of User Mention Objects*  
   
     Represents other Twitter users mentioned in the text of the Tweet.  
     The [entities](#entities) section will contain a **user_mentions** array containing an object for every **user mention** included in the Tweet body, and include an empty array if no user mention is present.
           
     Example:
     ```json
        {
          "user_mentions": [
            {
              "name": "Twitter API",
              "indices": [
                4,
                15
              ],
              "screen_name": "twitterapi",
              "id": 6253282,
              "id_str": "6253282"
            }
          ]
        }        
     ```
     [back](#Tweet-JSON-Schema)

       + ###### entities-user_mention-id  
          *Type: Int64*  
            
            ID of the mentioned user, as an integer.  
            
            Example:
            ```json
            "id":6253282
            ```
            [back](#Tweet-JSON-Schema)

        + ###### entities-user_mention-id_str  
          *Type: String*  
            
            ID of the mentioned user, as a string.  
            
            Example:
            ```json
            "id_str":"6253282"
            ```
            [back](#Tweet-JSON-Schema)

        + ###### entities-user_mention-indices  
          *Type: Array of Int*  
            
            An array of integers representing the offsets within the Tweet text where the user reference begins and ends. The first integer represents the location of the ‘@’ character of the user mention. The second integer represents the location of the first non-screenname character following the user mention.  
            
            Example:
            ```json
            "indices":[4,15]
            ```
            [back](#Tweet-JSON-Schema)

        + ###### entities-user_mention-name  
          *Type: String*  
            
            Display name of the referenced user.  
            
            Example:
            ```json
            "name":"Twitter API"
            ```
            [back](#Tweet-JSON-Schema)

        + ###### entities-user_mention-screen_name  
          *Type: String*  
            
            Screen name of the referenced user.   
            
            Example:
            ```json
            "screen_name":"twitterapi"
            ```
            [back](#Tweet-JSON-Schema)
-----------------------------
   + ##### entities-symbols  
     *Type: Array of Symbol Objects*  
   
     Represents symbols, i.e. $cashtags, included in the text of the Tweet.
     
     The [entities](#cashtag) section will contain a symbols array containing an object for every $cashtag included in the Tweet body, and include an empty array if no symbol is present.


           
     Example:
     ```json
        {
          "symbols": [
            {
              "indices": [
                12,
                17
              ],
              "text": "twtr"
            }
          ]
        }
     ```
     [back](#Tweet-JSON-Schema)

       + ###### entities-symbol-indices  
          *Type: Array of Int*  
            
            An array of integers indicating the offsets within the Tweet text where the symbol/cashtag begins and ends. The first integer represents the location of the $ character in the Tweet text string. The second integer represents the location of the first character after the cashtag. Therefore the difference between the two numbers will be the length of the hashtag name plus one (for the ‘$’ character)  
            
            Example:
            ```json
            "indices":[12,17]
            ```
            [back](#Tweet-JSON-Schema)

        + ###### entities-symbol-text  
          *Type: String*  
            
            Name of the cashhtag, minus the leading ‘$’ character.  
            
            Example:
            ```json
            "text":"twtr"
            ```
            [back](#Tweet-JSON-Schema)

-----------------------------
   + ##### entities-polls  
     *Type: Array of Symbol Objects*  
   
     Represents Twitter Polls included in the Tweet. 
     
     The entities section will contain a polls array containing a single poll object if the Tweet contains a poll. If no poll is included, there will be no polls array in the entities section.

     Note that these Poll metadata are only available with the following Enterprise APIs:
     + Volume streams ([Decahose](https://developer.twitter.com/en/docs/tweets/sample-realtime/overview/decahose))
     + [Real-time PowerTrack](https://developer.twitter.com/en/docs/tweets/filter-realtime/overview/powertrack-api)
     + [Historical PowerTrack](https://developer.twitter.com/en/docs/tweets/batch-historical/overview)
     + Twitter Search APIs ([Full-Archive Search](https://developer.twitter.com/en/docs/tweets/search/quick-start/enterprise-full-archive) and [30-Day Search]())    

           
     Example:
     ```json
        {"polls": [
              {
                "options": [
                  {
                    "position": 1,
                    "text": "I read documentation once."
                  },
                  {
                    "position": 2,
                    "text": "I read documentation twice."
                  },
                  {
                    "position": 3,
                    "text": "I read documentation over and over again."
                  }
                ],
                "end_datetime": "Thu May 25 22:20:27 +0000 2017",
                "duration_minutes": 60
              }
            ]
          }
     ```
     [back](#Tweet-JSON-Schema)

        + ###### entities-poll-options  
          *Type: Array of Option Object*  
            
            An array of options, each having a poll position, and the text for that position.  
            
            Example:
            ```json
            {"options": [
                      {
                        "position": 1,
                        "text": "I read documentation once."
                      }
                  ]
            }
            ```
            [back](#Tweet-JSON-Schema)

        + ###### entities-poll-end_datetime  
          *Type: String*  
            
            Time stamp (UTC) of when poll ends.  
            
            Example:
            ```json
            "end_datetime": "Thu May 25 22:20:27 +0000 2017"
            ```
            [back](#Tweet-JSON-Schema)

        + ###### entities-poll-duration_minutes  
          *Type: String*  
            
            Duration of poll in minutes.   
            
            Example:
            ```json
            "duration_minutes": 60
            ```
            [back](#Tweet-JSON-Schema)

-----------------------------
+ #### extended_entities
  When between one and four native photos or one video or one animated GIF are in Tweet, contains an array 'media' metadata. This is also available in Quote Tweets.  
  
  *Type: [Entities Media](#entities-media)*  

  [back](#Tweet-JSON-Schema)

     

-----------------------------
### Tweet-full-sample
Here is a full tweet JSON, that's mean that all JSON fields are filled.
This JSON serve just as a test to see all the fields. Indeed, from Twitter point of view it's not *correct** because the appearance of the fields depends on certain conditions and some are exclusive (if *field A* is present then *field B* cannot be present).

```json
{
  "created_at" : "Wed Oct 10 20:19:24 +0000 2018",
  "id" : 1050118621198921728,
  "id_str" : "1050118621198921728",
  "text" : "To make room for more expression, we will now count all emojis as equal—including those with gender‍‍‍ ‍‍and skin t… https://t.co/MkGjXf9aXm",
  "source" : "Twitter Web Client",
  "truncated" : true,
  "in_reply_to_status_id" : 1051222721923756032,
  "in_reply_to_status_id_str" : "1051222721923756032",
  "in_reply_to_user_id" : 6253282,
  "in_reply_to_user_id_str" : "6253282",
  "in_reply_to_screen_name" : "twitterapi",
  "user" : {
    "id" : 6253282,
    "id_str" : "6253282",
    "name" : "Twitter API",
    "screen_name" : "TwitterAPI",
    "location" : "San Francisco, CA",
    "derived" : {
      "locations" : [ {
        "country" : "United States",
        "country_code" : "US",
        "locality" : "Denver"
      } ]
    },
    "url" : "https://developer.twitter.com",
    "description" : "The Real Twitter API. Tweets about API changes, service issues and our Developer Platform. Don't get an answer? It's on my website.",
    "protected" : true,
    "verified" : true,
    "followers_count" : 6129794,
    "friends_count" : 12,
    "listed_count" : 12899,
    "favourites_count" : 31,
    "statuses_count" : 3658,
    "created_at" : "Wed May 23 06:01:13 +0000 2007",
    "profile_banner_url" : "https://pbs.twimg.com/profile_banners/6253282/1497491515",
    "profile_image_url_https" : "https://pbs.twimg.com/profile_images/942858479592554497/BbazLO9L_normal.jpg",
    "default_profile" : false,
    "default_profile_image" : false,
    "withheld_in_countries" : [ "GR", "HK", "MY" ],
    "withheld_scope" : "user"
  },
  "coordinates" : {
    "coordinates" : [ -75.143105, 40.05702 ],
    "type" : "Point"
  },
  "place" : {
    "id" : "01fbe706f872cb32",
    "url" : "http://api.twitter.com/1/geo/id/0172cb32.json",
    "place_type" : "city",
    "name" : "Washington",
    "full_name" : "Washington, DC",
    "country_code" : "US",
    "country" : "United States",
    "bounding_box" : {
      "coordinates" : [ [ [ -77.11976, 38.791645 ], [ -76.90939, 38.791645 ], [ -76.90939, 38.99555 ], [ -77.11976, 38.99555 ] ] ],
      "type" : "Polygon"
    },
    "attributes" : { }
  },
  "quoted_status_id" : 1050119905717055488,
  "quoted_status_id_str" : "1050119905717055488",
  "is_quote_status" : false,
  "quote_count" : 33,
  "reply_count" : 30,
  "retweet_count" : 160,
  "favorite_count" : 295,
  "entities" : {
    "hashtags" : [ {
      "indices" : [ 32, 38 ],
      "text" : "nodejs"
    } ],
    "media" : [ {
      "display_url" : "pic.twitter.com/5J1WJSRCy9",
      "expanded_url" : "https://twitter.com/nolan_test/status/930077847535812610/photo/1",
      "id" : 930077847535812610,
      "id_str" : "930077847535812610",
      "indices" : [ 13, 36 ],
      "media_url" : "http://pbs.twimg.com/media/DOhM30VVwAEpIHq.jpg",
      "media_url_https" : "https://pbs.twimg.com/media/DOhM30VVwAEpIHq.jpg",
      "sizes" : {
        "thumb" : {
          "w" : 150,
          "h" : 150,
          "resize" : "crop"
        },
        "large" : {
          "w" : 2048,
          "h" : 1366,
          "resize" : "fit"
        },
        "medium" : {
          "w" : 1200,
          "h" : 800,
          "resize" : "fit"
        },
        "small" : {
          "w" : 680,
          "h" : 454,
          "resize" : "fit"
        }
      },
      "source_status_id" : 205282515685081088,
      "source_status_id_str" : "205282515685081088",
      "type" : "photo",
      "url" : "https://t.co/5J1WJSRCy9",
      "additional_media_info" : {
        "title" : "#ATLvsNYJ: Tomlinson TD from McCown",
        "description" : "NFL",
        "embeddable" : false,
        "monetizable" : true
      },
      "video_info" : {
        "aspect_ratio" : [ 9, 16 ],
        "duration_millis" : 10704,
        "variants" : [ {
          "bitrate" : 320000,
          "content_type" : "video/mp4",
          "url" : "https://video.twimg.com/ext_tw_video/869317980307415040/pu/vid/180x320/FMei8yCw7yc_Z7e-.mp4"
        }, {
          "bitrate" : 2176000,
          "content_type" : "video/mp4",
          "url" : "https://video.twimg.com/ext_tw_video/869317980307415040/pu/vid/720x1280/octt5pFbISkef8RB.mp4"
        }, {
          "bitrate" : 832000,
          "content_type" : "video/mp4",
          "url" : "https://video.twimg.com/ext_tw_video/869317980307415040/pu/vid/360x640/2OmqK74SQ9jNX8mZ.mp4"
        }, {
          "content_type" : "application/x-mpegURL",
          "url" : "https://video.twimg.com/ext_tw_video/869317980307415040/pu/pl/wcJQJ2nxiFU4ZZng.m3u8"
        } ]
      }
    } ],
    "urls" : [ {
      "display_url" : "bit.ly/18gECvy",
      "expanded_url" : "http://bit.ly/18gECvy",
      "indices" : [ 62, 85 ],
      "url" : "https://t.co/D0n7a53c2l",
      "unwound" : {
        "url" : "https://www.youtube.com/watch?v=oHg5SJYRHA0",
        "status" : 200,
        "title" : "RickRoll'D",
        "description" : "http://www.facebook.com/rickroll548 As long as trolls are still trolling, the Rick will never stop rolling."
      }
    } ],
    "user_mentions" : [ {
      "id" : 6253282,
      "id_str" : "6253282",
      "indices" : [ 4, 15 ],
      "name" : "Twitter API",
      "screen_name" : "twitterapi"
    } ],
    "symbols" : [ {
      "indices" : [ 12, 17 ],
      "text" : "twtr"
    } ],
    "polls" : [ {
      "options" : [ {
        "position" : 1,
        "text" : "I read documentation once."
      }, {
        "position" : 2,
        "text" : "I read documentation twice."
      }, {
        "position" : 3,
        "text" : "I read documentation over and over again."
      } ],
      "end_datetime" : "Thu May 25 22:20:27 +0000 2017",
      "duration_minutes" : 60
    } ]
  },
  "extended_entities" : {
    "media" : [ {
      "display_url" : "pic.twitter.com/5J1WJSRCy9",
      "expanded_url" : "https://twitter.com/nolan_test/status/930077847535812610/photo/1",
      "id" : 930077847535812608,
      "id_str" : "930077847535812610",
      "indices" : [ 13, 36 ],
      "media_url" : "http://pbs.twimg.com/media/DOhM30VVwAEpIHq.jpg",
      "media_url_https" : "https://pbs.twimg.com/media/DOhM30VVwAEpIHq.jpg",
      "sizes" : {
        "thumb" : {
          "w" : 150,
          "h" : 150,
          "resize" : "crop"
        },
        "large" : {
          "w" : 2048,
          "h" : 1366,
          "resize" : "fit"
        },
        "medium" : {
          "w" : 1200,
          "h" : 800,
          "resize" : "fit"
        },
        "small" : {
          "w" : 680,
          "h" : 454,
          "resize" : "fit"
        }
      },
      "source_status_id" : 205282515685081088,
      "source_status_id_str" : "205282515685081088",
      "type" : "photo",
      "url" : "https://t.co/5J1WJSRCy9",
      "additional_media_info" : {
        "title" : "#ATLvsNYJ: Tomlinson TD from McCown",
        "description" : "NFL",
        "embeddable" : false,
        "monetizable" : true
      },
      "video_info" : {
        "aspect_ratio" : [ 9, 16 ],
        "duration_millis" : 10704,
        "variants" : [ {
          "bitrate" : 320000,
          "content_type" : "video/mp4",
          "url" : "https://video.twimg.com/ext_tw_video/869317980307415040/pu/vid/180x320/FMei8yCw7yc_Z7e-.mp4"
        }, {
          "bitrate" : 2176000,
          "content_type" : "video/mp4",
          "url" : "https://video.twimg.com/ext_tw_video/869317980307415040/pu/vid/720x1280/octt5pFbISkef8RB.mp4"
        }, {
          "bitrate" : 832000,
          "content_type" : "video/mp4",
          "url" : "https://video.twimg.com/ext_tw_video/869317980307415040/pu/vid/360x640/2OmqK74SQ9jNX8mZ.mp4"
        }, {
          "content_type" : "application/x-mpegURL",
          "url" : "https://video.twimg.com/ext_tw_video/869317980307415040/pu/pl/wcJQJ2nxiFU4ZZng.m3u8"
        } ]
      }
    } ]
  },
  "favorited" : true,
  "retweeted" : false,
  "possibly_sensitive" : false,
  "filter_level" : "low",
  "lang" : "en"
}
```
