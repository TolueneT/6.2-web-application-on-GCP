# GCP Project Documentation

## Static Website Deployment
### Using Google Cloud Storage
1. **Create a Cloud Storage Bucket:**
   - Navigate to Cloud Storage and create a new bucket.
     ![Screenshot of Deployment](images/image1)
   - Make the bucket public and configure it for website hosting.

2. **Upload Files:**
   - Upload your `index.html`, `styles.css`, and `script.js` files.

## API Service Setup

### Using Google Cloud Functions
1. **Enable Cloud Functions API:**
   - Enable the Cloud Functions API from the GCP Console.
2. **Create a Cloud Function:**
   - Create and deploy your function.
      - Name: 'simpleApi
      - Trigger: HTTP
      - Runtime: Node.js
3. **Deploy the function:**
     - Use the following code for your function:
        'exports.simpleApi = (req, res) => {
  res.set('Access-Control-Allow-Origin', '*');
  res.status(200).send('Hello from the API!');
};'

      - Click "Deploy"


## Integration
- Ensure the static website fetches data from the API and displays it correctly.
  - Modify static website's JavaScript to call the API
     '''<script>
fetch('https://REGION-PROJECT_ID.cloudfunctions.net/simpleApi')  // or your App Engine API endpoint
  .then(response => response.json())
  .then(data => {
    document.getElementById('api-message').innerText = data.message;
  })
  .catch(error => console.error('Error:', error));
</script>'''


## Testing
- Open your website URL and verify the API data is fetched and displayed as expected.
