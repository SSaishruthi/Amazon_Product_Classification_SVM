# Amazon_Product_Classification_SVM

Dataset used - Amazon review data - UCSD dataset

Data PreProcessing

- Features selection: We need only information about product title and distinct categories the
  product belongs. So, all the other features were dropped.
- Handling null values: drop the rows with null values in Product title or categories columns.
- Data Transformation: created a new variable Category path using Categories column.
  Obtain the first path from categories list of lists, giving it top priority and add it as Category
  path. For categories like Books the title is not given. such categories should be excluded.
  Now in list of all categories, excluded the non-deepest category as more deeper categories
  will lead to more relevant search. for this, we sort our categories path and compare each
  other and retain deepest categories.
- Handling Product title: Title can be long and contain unimportant words. Normalized the
  data using Unicode retain data having different canonical meaning. Html parser to remove
  any tags. Removing stop words from product.
  
  Most of the records in the dataset are mapped to more than one categories. The categories label contains a list of values of all     
  the categories where the product is currently positioned. Also worked prepared another model only using the Clothing, shoes and 
  Jewelry data set that was pre-processed to factor in multiple categories for a product. A combined category was created for    
  products that are mapped to more than one category.
  The combined categories prepared have unique titles for each title. i.e. 1st category dataset just has the records that have the   
  1st category value and doesn't contain records that have 2nd or 3rd category. Similarly, the 2nd category datasets have titles 
  that have only two categories but doesn’t contain 3rd category.
  
  Method
  
 - Training and testdata size is split in ratio of 90% and 10%.
 - Product title is vectorized using Count vectorizer and the category path is labelled using Label encoder.
 - Using fit transform and transform, both training and test data are vectorized.
 - Train the classifier using X_train and Y_train and predict for X_test.
 - To compute accuracy, we are predicting the categories of the test dataset and then computing
   accuracy based on the predicted values and actual values.
