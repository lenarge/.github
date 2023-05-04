# Lenarge Public API

Welcome to Lenarge API! This is the README file for our homepage, which provides information on how to use our API Public endpoints.

```
PRODUCTION API Url: https://api.lenarge.com.br
STAGING API Url: https://api.dev.lenarge.com.br
```

## Authentication

Our API uses the Header Authorization model with the Bearer API_KEY authentication method. To authenticate your requests, you must include your API key in the Authorization header of your HTTP request. The header should be in the following format:

```
Authorization: Bearer YOUR_API_KEY
```

## SHIPPER Endpoints

The Shipper endpoints provide access to features related to the shipping operations. The following endpoint is available for use with our API:

### GET /shipper/operations/:OPERATION_FRIENDLY_ID/vehicle_tracking

This endpoint allows you to track the location and status of vehicles that are involved in a specific shipping operation. The `OPERATION_FRIENDLY_ID` parameter is a string that represents the operation in question, which is sent to the client via email along with the API key.

Example Response:

```typescript
interface VehicleTrackingResponse {
  vehicleTrackingItems: Array<{
    truck: {
      licensePlate: string;
      brandName: string;
      modelName: string;
      modelYear: string;
      manYear: string;
    };
    trailers: {
      licensePlate: string;
      brandName: string;
      modelType: string;
      modelYear: string;
      manYear: string;
    }[];
    city: string;
    // GeoJSON Point: https://www.rfc-editor.org/rfc/rfc7946#appendix-A.1
    location: {
      coordinates: [number, number]; // longitude, latitude
      type: "Point";
    };
    engineOn: boolean;
  }>;
}
```

Example:

```json
{
    "vehicleTrackingItems": [
        {
            "truck": {
                "licensePlate": "RJO5B70",
                "brandName": "VOLVO",
                "modelName": "FH 500 6X2T",
                "modelYear": "2022",
                "manYear": "2021"
            },
            "trailers": [
                {
                    "licensePlate": "PWB7717",
                    "brandName": "ROSSETTI",
                    "modelType": "CARRETA BASCULANTE VANDERLEIA",
                    "modelYear": "2015",
                    "manYear": "2015"
                }
            ],
            "city": "Nova Lima/MG",
            "location": {
                "coordinates": [
                    -43.9553303,
                    -20.1583173
                ],
                "type": "Point"
            },
            "engineOn": false
        }
    ]
}
```

The response includes an array of `vehicleTrackingItems`, which contain information about the tracked vehicle(s). Each `vehicleTrackingItem` includes details about the truck and trailer(s), as well as the current location of the vehicle and whether the engine is on.

## Conclusion

We hope this information is helpful for using our API. If you have any questions or concerns, please contact us with english or portuguese at suporte.ti@lenarge.com.br.
