# glowfishapi
The Glowfish PHP API Library

For detailed examples and instructions on using the Glowfish RESTful API, please visit https://glow.fish/docs. 

## Example 1 - Posting/Creating a Lead

	<?php
		require_once("Colugo/API/API.php");
		$user = new \Colugo\API\User("me@myemail.com", "XXXXXX");
		$api = new \Colugo\API\API($user);
		// create a new lead
		$lead = new \Colugo\API\Lead();
		$lead->setLeadSource("My Leads");
		$lead->setLeadIpAddress("127.0.0.1");
		$lead->setFields([
			"First Name" => "John",
			"Last Name" => "Smith",
			"Address 1" => "123 Fake Street",
			"Zip" => "12498",
			"Mobile Phone" => "(555) 555-5555",
			"Email" => "jsmith@gmail.com"
		]);
		try {
			$api->create($lead);
		} catch (\Exception $e) {
			echo "Error Raised: ", $e->getMessage(), "\n";
			exit(0);
		}
		// output the lead
		echo json_encode($lead, JSON_PRETTY_PRINT), "\n";
