Praying For You : An application to help manage prayer requests, testimonies, 
groups, partners and schedules. 

This project uses PouchDB to store user data with CouchDB replication.  

Users can submit prayer requests or testimonies.  Testimonies can be linked to 
specific prayer requests using "answered prayer" feature.  Prayer requests
and testimonies can by searched using #hashtags.  Any prayer request a user
submits automatically becomes part of that user's personal prayer list and that
user can also submit requests to any prayer group to which he/she belongs.
A user can add any prayer request to his/her personal prayer list.  Users
can request to become prayer partners with other users.  Prayer partners can
coordinate schedules for when they are available to pray together.  They may
pray invidually at a certain time or get togehter in person or over the phone
ffor internet.  A user can create or join a prayer group.  A prayer group 
can be public or private.  Private prayer groups can be joined on the invitation
by or with permission of the group owner or designated moderators.  Only members
of private groups can read or post to private groups.

Prayer requests:

Users can submit prayer requests.  #Hashtags can be embedded.  

{_id:342, user:"JohnDoe", request:"A #family request for #healing.  My cousin has #cancer"}

The user interface will have the ability to auto generate certain prayer request 
phrases using common tags.  For example:

  Praying for:
  [ ] #personal
  [x] #family
  [ ] #church
  [ ] #churchmember
  [ ] #friend
  [ ] #community

  Who needs:
  [x] #healing
  [ ] #finances
  [ ] #relationships
  [ ] #encourgement
  [ ] #spirituality
  [ ] #ministry

A prayer request can be private or public.  If a prayer request is private than
only those the user shares the request with can see it.

requests=[...
{_id:342, user:"JohnDoe", visibility:"public", 
  request:"A #family request for #healing.  My cousin has #cancer"},

{_id:343, user:"JohnDoe", visibility:"private", 
  request:"A #family request for #relationships.  My #wife asked for a #divorce"}
  ...]

A prayer request can be shared with a prayer partner or prayer group.  Users
can give permission to the people or group they share requests to also share
those same requests.  That new person can only read but cannot further share
the request.  Here is an example where John Doe shares his request with Deacaon
Blue giving Deacon Blue permission to share.  Deacon Blue shares it with Pastor
Brown.  But Pastor Brown doesn't have automatic sharing permission.

shares=[...
{_id:245, request:343, sharedwith:"deaconblue", canshare:"true"},
{_id:246, request:343, sharedwith:"pastorbrown", canshare:"false"}...]

Say if John Doe decides to share this request with Pastor Brown.  The app first
checks to see if it's already been shared with him.  If the user grants Pastor
Brown sharing privileges the share is updated to reflect that.  Otherwise
nothing changes.

shares=[...
{_id:245, request:343, sharedwith:"deaconblue", canshare:"true"},
{_id:246, request:343, sharedwith:"pastorbrown", canshare:"true"}...]

Prayer testimonies:

A testimony can be linked to a prayer request or stand alone.  Testmonies are
linked using the "answered prayer" feature.

- Linked
{_id:75, user:"JohnDoe", request:342, testimony : "My cousin is getting a new
experimental cancer treatment that seems to be working"}

- Stand alone

{_id:76, user:"JohnDoe", testimony : "A friend who I had given
up on called today to say he accepted Jesus!  Praise God for #salvation!"}

Prayer answers:

When a user is reviewing the prayer requests he/she has submitted, that user
can click the "answer" button that will generate a linked testimony.

 Prayer Request: A #family request for #healing.  My cousin has #cancer.
 [Answer]
 
Prayer lists:

Any prayer request a user makes is automatically added to his/her prayer list.
Users can also add prayer requests of others to their personal list either by
searching the prayer request database or through the prayer lists of their
prayer partners or groups.

Prayer partners:

People become prayer partners simiarly to how they become friends on Facebook.
Someone sends a partner request and the person receiving the request can 
accept or deny it.  Prayer partners can coordinate their schedules by giving
each other times and days they are available to pray.

Prayer groups:

Users can create and/or join groups.  Group members can submit their prayer
requests and testimonies to the group.  Groups can be open or closed.  Anyone
can join an open group.  Closed groups can only be joined by invitation or with
permission from the group owner.  If a group owner sends a user an invite, that
user can join simply by accepting the invite.  If a user who has not been
invited requests to join a group, that request can only be accepted by the 
group owner or other moderators the owner designates.  Anyone can read the
requests and testimonies of an open group.  Only group members can read the
requests and testimonies of a closed group.  Private prayer requests can only
be submitted to a closed group.
