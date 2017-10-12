PredictionIO (Universal Recommendations) for Magento
=============

Magento Upsell Product Enhancement, Recommendation with PredictionIO 0.11

## Install

Clone the git repo - modman clone https://github.com/<current_repo>/Predictionio.git

### Requirements

Must have an instance of PredictionIO server setup and ready to accept data. Please see the docs for information.

### Features

* Replace upsell products with products defined by PredictionIO 
* Reverts to admin defined upsells when there is no data returned by PredictionIO (not implemented)
* Product View Actions
* Product Sale Actions
* Product Review Actions (not implemented)
* Guest Action Logging
* Import Existing Sales

#### Replacing Upsell Products

Configure the module to make API calls to your instance of PredictionIO, defining the host, port and engine (name and key) and data will be recorded when the user is logged in.

#### Revert to Default Upsells (not implemented)

When the module is disabled or the user is not logged in or PredictionIO has not returned any matching products then the module will silently revert to magento's built in upsell products allowing store admin to set these manually.

#### Product View Actions

When a customer views a product page the module will make an API call to add the product to the PredictionIO server as well as record the action of view

#### Product Sale Actions

When a customer places as an order then the module will get the parent product of the purchased simple product if available and post its ID to PredictionIO as only parent products can show the upsells.

#### Product Review Actions (not implemented)

When a customer reviews a product the module will get the average rating from all available ratings then make an API call to add the product rating to the PredictionIO server as well as record the action of rate

#### Guest Action Logging

Sometimes customers don't login till they get to the checkout so we log the customers actions in the session to post to PredictionIO when the customer logs in.

#### Import Existing Sales

Using the shell script included you can import all exiting sales data i.e Customers, Products and the action of conversion to kick start your data feeds. Just run the following command from your web root- 

``cp shell/backlogload.php {{base_dir}}/shell/

php shell/backlogload.php --stores store1,store2``

Where --stores looks for a comma seperated list of store names to import from. If you don't supply `--stores` then all stores in your Magento installation will be imported.

#### PredictionIO

* Web: [https://predictionio.incubator.apache.org]
* Docs: [https://predictionio.incubator.apache.org/start/]
* Twitter: https://twitter.com/apachepio

#### Authors

* Magento Module was originally developed by Steven Richardson - https://twitter.com/troongizmo
* Updated for PredictionIO 0.11.0 and Universal Recommender by Dima Kovalyov - dimdroll@gmail.com

  [https://predictionio.incubator.apache.org/start/]: https://predictionio.incubator.apache.org/start/
  [http://www.actionml.com/docs/ur]: http://www.actionml.com/docs/ur
