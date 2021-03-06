INSTRUCTIONS
=============

1. Go to these locations:

   a. showing Musicbrainz_ getting metadata (given an artist, all the albums + all songs of artist): `plexstuff.plexmusic.plexmusic.get_music_metadata <get_music_metadata_>`_

   b. showing choose the correct YouTube clip: `plexstuff.plexmusic.plexmusic.youtube_search <youtube_search_>`_
      
   c. showing part of downloading from `youtube-dl`: `plexstuff.plexmusic.plexmusic.get_youtube_file <get_youtube_file_>`_

2. ``plex_music_songs`` documentation at `this website`_.
      
3. Show animation of getting songs, ``plex_music_songs_download_artist_songs.mp4``, with video viewer.

4. Show how to get ``All I Need`` by ``Air``

   .. code-block:: console

      plex_music_songs -a Air -s "All I Need" --musicbrainz

   Which can take a bit of time.
   
.. _MusicBrainz: https://musicbrainz.org
		   
.. _`get_music_metadata`: https://github.com/tanimislam/plexstuff/blob/37cfb9f9e52864d8bdd6a2e154dc93b48ff2c908/plexstuff/plexmusic/plexmusic.py#L411

.. _`youtube_search`: https://github.com/tanimislam/plexstuff/blob/37cfb9f9e52864d8bdd6a2e154dc93b48ff2c908/plexstuff/plexmusic/plexmusic.py#L888

.. _`youtube-dl`: https://rg3.github.io/youtube-dl

.. _`this website`: https://plexstuff.readthedocs.io/plex-music/cli_tools/plex_music_cli.html?highlight=plex_music_songs#plex-music-songs

.. _`get_youtube_file`: https://github.com/tanimislam/plexstuff/blob/37cfb9f9e52864d8bdd6a2e154dc93b48ff2c908/plexstuff/plexmusic/plexmusic.py#L848
