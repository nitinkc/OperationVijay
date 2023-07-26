
## Music Store DB Documentation

### Introduction

This document outlines the updated requirements for the development of a music store database management system. The system will handle various aspects of a music store, including playlists, invoices, customers, employees, tracks, albums, artists, media types, and genres. The primary goal is to create an efficient and user-friendly platform that will facilitate music inventory management, sales, and customer interactions.

### Table Definitions

1. **PlaylistTrack** Table
   - *Description*: This table will store the associations between playlists and tracks.
   - *Attributes*:
     - `PlaylistId` (Foreign Key): References the `Playlist` table to link the playlist to a specific track.
     - `TrackId` (Foreign Key): References the `Track` table to link the track to a specific playlist.
   - *Constraints*:
     - `PK_PlaylistTrack`: Primary key constraint on `PlaylistId` and `TrackId` to ensure unique associations.

2. **Playlist** Table
   - *Description*: This table will store information about playlists created by customers or employees.
   - *Attributes*:
     - `PlaylistId` (Primary Key): Unique identifier for each playlist.
     - `Name`: The name of the playlist.
   - *Constraints*:
     - `PK_Playlist`: Primary key constraint on `PlaylistId` to ensure uniqueness.

3. **InvoiceLine** Table
   - *Description*: This table will store individual line items of an invoice, representing a track purchase.
   - *Attributes*:
     - `InvoiceLineId` (Primary Key): Unique identifier for each invoice line item.
     - `InvoiceId` (Foreign Key): References the `Invoice` table to link the line item to a specific invoice.
     - `TrackId` (Foreign Key): References the `Track` table to identify the purchased track.
     - `UnitPrice`: The price of the track at the time of purchase.
     - `Quantity`: The quantity of the track purchased.
   - *Constraints*:
     - `PK_InvoiceLine`: Primary key constraint on `InvoiceLineId` to ensure uniqueness.

4. **Invoice** Table
   - *Description*: This table will store information about customer invoices.
   - *Attributes*:
     - `InvoiceId` (Primary Key): Unique identifier for each invoice.
     - `CustomerId` (Foreign Key): References the `Customer` table to identify the customer associated with the invoice.
     - `InvoiceDate`: The date when the invoice was issued.
     - `BillingAddress`: The billing address for the invoice.
     - `BillingCity`: The billing city for the invoice.
     - `BillingState`: The billing state for the invoice.
     - `BillingCountry`: The billing country for the invoice.
     - `BillingPostalCode`: The billing postal code for the invoice.
     - `Total`: The total amount of the invoice.
   - *Constraints*:
     - `PK_Invoice`: Primary key constraint on `InvoiceId` to ensure uniqueness.

5. **Customer** Table
   - *Description*: This table will store information about the store's customers.
   - *Attributes*:
     - `CustomerId` (Primary Key): Unique identifier for each customer.
     - `FirstName`: The first name of the customer.
     - `LastName`: The last name of the customer.
     - `Company`: The company associated with the customer.
     - `Address`: The address of the customer.
     - `City`: The city of the customer.
     - `State`: The state of the customer.
     - `Country`: The country of the customer.
     - `PostalCode`: The postal code of the customer.
     - `Phone`: The phone number of the customer.
     - `Fax`: The fax number of the customer.
     - `Email`: The email address of the customer.
     - `SupportRepId` (Foreign Key): References the `Employee` table to identify the support representative for the customer.
   - *Constraints*:
     - `PK_Customer`: Primary key constraint on `CustomerId` to ensure uniqueness.
     - `FK_CustomerSupportRepId`: Foreign key constraint on `SupportRepId` referencing the `Employee` table.

6. **Employee** Table
   - *Description*: This table will store information about the store's employees.
   - *Attributes*:
     - `EmployeeId` (Primary Key): Unique identifier for each employee.
     - `LastName`: The last name of the employee.
     - `FirstName`: The first name of the employee.
     - `Title`: The job title of the employee.
     - `ReportsTo` (Foreign Key): References the `Employee` table to identify the manager of the employee.
     - `BirthDate`: The birth date of the employee.
     - `HireDate`: The hire date of the employee.
     - `Address`: The address of the employee.
     - `City`: The city of the employee.
     - `State`: The state of the employee.
     - `Country`: The country of the employee.
     - `PostalCode`: The postal code of the employee.
     - `Phone`: The phone number of the employee.
     - `Fax`: The fax number of the employee.
     - `Email`: The email address of the employee.
   - *Constraints*:
     - `PK_Employee`: Primary key constraint on `EmployeeId` to ensure uniqueness.
     - `FK_EmployeeReportsTo`: Foreign key constraint on `ReportsTo` referencing the `Employee` table.

7. **Genre** Table
   - *Description*: This table will store information about music genres.
   - *Attributes*:
     - `GenreId` (Primary Key): Unique identifier for each genre.
     - `Name`: The name of the genre.
   - *Constraints*:
     - `PK_Genre`: Primary key constraint on `GenreId` to ensure uniqueness.

8. **MediaType** Table
   - *Description*: This table will store information about different types of media used for music tracks (e.g., MP3, AAC, etc.).
   - *Attributes*:
     - `MediaTypeId` (Primary Key): Unique identifier for each media type.
     - `Name`: The name of the media type.
   - *Constraints*:
     - `PK_MediaType`: Primary key constraint on `MediaTypeId` to ensure uniqueness.

9. **Album** Table
   - *Description*: This table will store information about music albums.
   - *Attributes*:
     - `AlbumId` (Primary Key): Unique identifier for each album.
     - `Title`: The title of the album.
     - `ArtistId` (Foreign Key): References the `Artist` table to identify the artist or band behind the album.
   - *Constraints*:
     - `PK_Album`: Primary key constraint on `AlbumId` to ensure uniqueness.
     - `FK_AlbumArtistId`: Foreign key constraint on `ArtistId` referencing the `Artist` table.

10. **Artist** Table
    - *Description*: This table will store information about music artists or bands.
    - *Attributes*:
      - `ArtistId` (Primary Key): Unique identifier for each artist.
      - `Name`: The name of the artist or band.
    - *Constraints*:
      - `PK

_Artist`: Primary key constraint on `ArtistId` to ensure uniqueness.

11. **Track** Table
    - *Description*: This table will store information about individual music tracks.
    - *Attributes*:
      - `TrackId` (Primary Key): Unique identifier for each track.
      - `Name`: The name of the track.
      - `AlbumId`: References the `Album` table to link the track to a specific album.
      - `MediaTypeId`: References the `MediaType` table to identify the type of media (e.g., MP3, AAC, etc.).
      - `GenreId`: References the `Genre` table to categorize the track's genre.
      - `Composer`: The composer of the track.
      - `Milliseconds`: The duration of the track in milliseconds.
      - `Bytes`: The size of the track file in bytes.
      - `UnitPrice`: The price of the track for purchase.
    - *Constraints*:
      - `PK_Track`: Primary key constraint on `TrackId` to ensure uniqueness.
      - `FK_TrackAlbumId`: Foreign key constraint on `AlbumId` referencing the `Album` table.
      - `FK_TrackGenreId`: Foreign key constraint on `GenreId` referencing the `Genre` table.
      - `FK_TrackMediaTypeId`: Foreign key constraint on `MediaTypeId` referencing the `MediaType` table.

### Conclusion

The outlined requirement documentation provides a foundation for the development of a comprehensive music store database management system. The defined tables and their attributes will enable efficient storage and retrieval of music-related data, facilitating inventory management, sales, and customer interactions. The system aims to enhance the overall music store experience for both customers and employees.