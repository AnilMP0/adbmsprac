C:\Users\Anil Patel>mongoimport --db fifa --collection data --type csv --file "C:\Users\Anil Patel\OneDrive\Documents\WorldCups.csv" --headerline
2024-03-06T20:04:52.317+0530    connected to: mongodb://localhost/
2024-03-06T20:04:52.329+0530    20 document(s) imported successfully. 0 document(s) failed to import.

C:\Users\Anil Patel>mongosh
Current Mongosh Log ID: 65e883aac485007eeb3d8dff
Connecting to:          mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.1.5
Using MongoDB:          7.0.6
Using Mongosh:          2.1.5

For mongosh info see: https://docs.mongodb.com/mongodb-shell/

------
   The server generated these startup warnings when booting
   2024-03-01T21:59:31.003+05:30: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
------

test> use fifa
switched to db fifa
fifa> db.data.find({"Winner" : "Brazil"})
[
  {
    _id: ObjectId('65e87f0c767a57a67e642c84'),
    Year: 1958,
    Country: 'Sweden',
    Winner: 'Brazil',
    'Runners-Up': 'Sweden',
    Third: 'France',
    Fourth: 'Germany FR',
    GoalsScored: 126,
    QualifiedTeams: 16,
    MatchesPlayed: 35,
    Attendance: 819.81
  },
  {
    _id: ObjectId('65e87f0c767a57a67e642c85'),
    Year: 1962,
    Country: 'Chile',
    Winner: 'Brazil',
    'Runners-Up': 'Czechoslovakia',
    Third: 'Chile',
    Fourth: 'Yugoslavia',
    GoalsScored: 89,
    QualifiedTeams: 16,
    MatchesPlayed: 32,
    Attendance: 893.172
  },
  {
    _id: ObjectId('65e87f0c767a57a67e642c87'),
    Year: 1970,
    Country: 'Mexico',
    Winner: 'Brazil',
    'Runners-Up': 'Italy',
    Third: 'Germany FR',
    Fourth: 'Uruguay',
    GoalsScored: 95,
    QualifiedTeams: 16,
    MatchesPlayed: 32,
    Attendance: '1.603.975'
  },
  {
    _id: ObjectId('65e87f0c767a57a67e642c8d'),
    Year: 1994,
    Country: 'USA',
    Winner: 'Brazil',
    'Runners-Up': 'Italy',
    Third: 'Sweden',
    Fourth: 'Bulgaria',
    GoalsScored: 141,
    QualifiedTeams: 24,
    MatchesPlayed: 52,
    Attendance: '3.587.538'
  },
  {
    _id: ObjectId('65e87f0c767a57a67e642c8f'),
    Year: 2002,
    Country: 'Korea/Japan',
    Winner: 'Brazil',
    'Runners-Up': 'Germany',
    Third: 'Turkey',
    Fourth: 'Korea Republic',
    GoalsScored: 161,
    QualifiedTeams: 32,
    MatchesPlayed: 64,
    Attendance: '2.705.197'
  }
]
fifa> db.data.find({"Winner" : "Brazil"}).count()
5
fifa> db.data.find({"Year" : {"$gt":2005}} ,{_id:0,Winner:1})
[ { Winner: 'Italy' }, { Winner: 'Spain' }, { Winner: 'Germany' } ]
]
fifa> db.data.find({"Year" : {"$gt":1950}},{_id:0,Third:1})
[
  { Third: 'Austria' },
  { Third: 'France' },
  { Third: 'Chile' },
  { Third: 'Portugal' },
  { Third: 'Germany FR' },
  { Third: 'Poland' },
  { Third: 'Brazil' },
  { Third: 'Poland' },
  { Third: 'France' },
  { Third: 'Italy' },
  { Third: 'Sweden' },
  { Third: 'Croatia' },
  { Third: 'Turkey' },
  { Third: 'Germany' },
  { Third: 'Germany' },
  { Third: 'Netherlands' }
]
fifa> db.data.find({"GoalsScored" : {"$gt":140}},{_id:0,Year:1})
[
  { Year: 1982 },
  { Year: 1994 },
  { Year: 1998 },
  { Year: 2002 },
  { Year: 2006 },
  { Year: 2010 },
  { Year: 2014 }
]
