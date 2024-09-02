#azure
Azure blob storage is a powerful cloud based storage provided by microsoft azure

## Azure Blob Storage
1)blob storage is it structured, semi structured or unstructured storage
1. What for we use Azure BLOB storages (use cases) ---- we use it to store large amount of unstructured data such as files
 - Media files storage
 - Content distrubution
 - Big data analytics
1. How to connect from the app
- instal package
- 
1. What types of services can be used
- **Block Blobs**:
    
    - Used for storing text and binary data.
    - Ideal for large files that need to be uploaded and stored in smaller blocks, which can be managed individually.
    - Commonly used for documents, media files, backups, etc.
- **Append Blobs**:
    
    - Optimized for append operations.
    - Suitable for scenarios where data is constantly being appended, such as logging.
    - Each append operation is atomic, ensuring no data corruption in concurrent write scenarios.
- **Page Blobs**:
    
    - Designed for random read/write operations.
    - Used for scenarios requiring high I/O operations, such as virtual hard disk (VHD) files used by virtual machines.
    - Allows random access to pages of data within the blob.
https://learn.microsoft.com/en-us/rest/api/storageservices/understanding-block-blobs--append-blobs--and-page-blobs
https://www.youtube.com/watch?v=zivccBj7398&ab_channel=ExamPro


