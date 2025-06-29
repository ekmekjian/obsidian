#kotlin #client
![[NASA Open API#^282b27]]
## Goal
Create a desktop client that can pull NASA's open APIs.
- [ ] Create UI with [JetBrains Compose](https://github.com/JetBrains/compose-jb/)
## APIs
### APO(Astronomy Picture of the Day)
#### Query Parameters
| Parameter   | Type       | Default  | Description                                                                                                            |
| ---------- | ---------- | -------- | ---------------------------------------------------------------------------------------------------------------------- |
| `date`       | YYYY-MM-DD | today    | The date of the APOD image to retrieve                                                                                 |
| `start_date` | YYYY-MM-DD | none     | The satrt of a date range, when requesting date for a range of dates. Cannot be used with date                         |
| `end_date`   | YYYY-MM-DD | today    | The end of the date range, when used with `start_date`                                                                 |
| `count`      | int        | none     | If this is specified then `count` randomly chosen images will be returned. Cannot be used with `date` or `start_date`. |
| `thumbs`     | bool       | False    | Return the URL of video thumbnail. If an APOD is not a video, this parameter is ignored                                |
| `api_key`    | string     | DEMO_KEY | api.nasa.gov key for expanded usage                                                                                                                       |
#### Returned Fields
Returns JSON

| Return Parameter | Type       | Description                                                                                                                                                                                                                                     |
| ---------------- | ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `resource`       | dictionary | describing `image_set` or `planet` that the response illustrates, completely determined by the structured endpoint                                                                                                                              |
| `concept_tages`  | bool       | A boolean reflection of the supplied option. included in response because of default values. **`concept_tags` are now disabled in this service. Also, an optional return parameter _copyright_ is returned if the image is not public domain.** |
| `title`          | string     | The title of the image.                                                                                                                                                                                                                         |
| `date`           | string     | Date of image. Included in response because of default values                                                                                                                                                                                   |
| `url`            | string     | The URL of the APOD image or video of the day.                                                                                                                                                                                                  |
| `hdurl`          | string     | The URL for any high-resolution image for that day. Returned regardless of 'hd' param setting but will be omitted in the response if it does not exist originally at APOD                                                                       |
| `media_type`     | string     | The type of media(data) returned. May either be 'image' or 'video' depending on content                                                                                                                                                         |
| `explanation`    | string     | The supplied text explanation of the image.                                                                                                                                                                                                     |
| `concepts`       | string     | The most relevant concepts within the text explanation. Only supplied if `concept_tags` is set to True.                                                                                                                                         |
| `thumbnail_url`  | string     | The URL of Thumbnail of the video.                                                                                                                                                                                                              |
| `copyright`      | String     | The name of the copyright holder.                                                                                                                                                                                                               |
| `service_version`| string     | The service version used.                                                                                                                                                                                                                       |
