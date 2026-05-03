
import json
def lambda_handler(event, context):
    a = event.get('num1', 0)
    b = event.get('num2', 0)
    result = a + b
    return {
        'statusCode': 200,
        'body': json.dumps({
            'sum': result
        })
    }







import boto3
from uuid import uuid4

def lambda_handler(event, context):
    s3 = boto3.client("s3")
    dynamodb = boto3.resource("dynamodb")
    dynamoTable = dynamodb.Table("newtable")

    # Check if the 'Records' key is present in the event
    if "Records" in event:
        for record in event["Records"]:
            bucket_name = record["s3"]["bucket"]["name"]
            object_key = record["s3"]["object"]["key"]
            size = record["s3"]["object"].get("size", -1)
            event_name = record.get("eventName", "Unknown")
            event_time = record.get("eventTime", "Unknown")

            dynamoTable.put_item(
                Item={
                    "unique": str(uuid4()),
                    "Bucket": bucket_name,
                    "Object": object_key,
                    "Size": size,
                    "Event": event_name,
                    "EventTime": event_time,
                }
            )
    else:
        print("No 'Records' key found in the event.")




